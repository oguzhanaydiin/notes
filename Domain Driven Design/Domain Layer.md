# Domain Layer

## SeedWork
Burası Domainimizde kullanılacak objelerin içerisinde olacağı bir klasör olacak (Base Entity, Value Object, AggregateRoot vs).

* Base Entity
Base Entityler projemizdeki kimliği olan objelerdir.

```
public abstract class BaseEntity
{
    public virtual Guid Id { get; set; }
    public DateTime CreateDate { get; set; }

    int? _requestedHashCode;

    private List<INotification> domainEvents;
    public IReadOnlyCollection<INotification> DomainEvents => domainEvents?.AsReadOnly();

    public void AddDomainEvent(INotification eventItem)
    {
        domainEvents = domainEvents ?? new List<INotification>();
        domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(INotification eventItem)
    {
        domainEvents?.Remove(eventItem);
    }

    public void ClearDomainEvents()
    {
        domainEvents?.Clear();
    }

    public bool IsTransient()
    {
        return Id == default;
    }

    public override bool Equals(object? obj)
    {
        if (obj == null || !(obj is BaseEntity))
            return false;

        if (ReferenceEquals(this, obj))
            return true;

        if (GetType() != obj.GetType())
            return false;

        BaseEntity item = (BaseEntity)obj;

        if (item.IsTransient() || IsTransient())
            return false;
        else
            return item.Id == Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = Id.GetHashCode() ^ 31; //XOR for random distribution

            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(BaseEntity left, BaseEntity right)
    {
        if (Equals(left, null))
            return Equals(right, null) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(BaseEntity left, BaseEntity right)
    {
        return !(left == right);
    }
}
```

* Value Object
Bunlar bizim projemizde kimliği olmayan projelerimiz olacak. Kimliği olmayan objelerin bazı fonksiyonları (birbirleriyle karşılaştırılmaları gibi) gerçekleştirmeleri zor olacağı için kendi sınıfı içerisinde bunları da içerecektir.

```
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !EqualOperator(left, right);
    }

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }

    public ValueObject GetCopy()
    {
        return MemberwiseClone() as ValueObject;
    }
}

```

* Aggregate Root:
Aggregate rootlar içerisinde birbiri olmadan düşünülemez objeleri barındırır. Mesela bir sipariş ve siparişin içindeki ürünlerin listesi gibi. Transaction bütünlüğünü ve bunlar arasındaki iş kurallarının da yürütülmesini sağlayacaktır.

```
public interface IAggregateRoot
{
}
```

* Repository:
Repository pattern ile tanıdığımız, bir base entity ile database arası işlemlerin yürütüldüğü yerdir.

```
public interface IRepository<T>
{
    IUnitOfWork UnitOfWork { get; }
}
```

* Unit Of Work:
Repositorylerimizin transactionlarının yönetildiği son aşamadır. Kaydedilmesi, roll back yapılması gibi işlemlerde kullanılabilir.
```
public interface IUnitOfWork : IDisposable
{
    Task<int> SaveChangesAsync(CancellationToken cancellationToken = default(CancellationToken));
    Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken));
}
```

## Aggregate Models



## Exceptions
Exception larımızı buradaki klasörde tutacağız. Projemize custome exceptionlar yazmak istersek aşağıdaki örnekteki gibi yazacağız. Exception classından türetip bu üç constructor'ı yazmamız yeterli.

```
public class OrderDomainExceptions : Exception
{
    public OrderDomainExceptions()
    {

    }

    public OrderDomainExceptions(string message) : base(message)
    {

    }

    public OrderDomainExceptions(string message, Exception innerException) : base(message, innerException)
    {

    }
}

```

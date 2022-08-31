# Graylog

## Adding GrayLog to a Project

Add serilog graylog to your project config.

```
<ItemGroup>
	<PackageReference Include="Serilog" Version="2.10.0" />
	<PackageReference Include="Serilog.AspNetCore" Version="4.1.0" />
	<PackageReference Include="Serilog.Sinks.Console" Version="3.1.1" />
	<PackageReference Include="Serilog.Sinks.Graylog" Version="2.2.2" />
</ItemGroup>
```
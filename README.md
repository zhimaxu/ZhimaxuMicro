# ZhimaxuMicroService

## docker 注意事项
> 本地运行时需要配置ssl证书
>> 1.可以参考[官网](https://learn.microsoft.com/zh-cn/aspnet/core/security/docker-https?view=aspnetcore-9.0)  
>> 2.也可以直接使用以下方式 
>>> ```cmd
>>> dotnet dev-certs https -ep ${HOME}/.aspnet/https/aspnetapp.pfx -p <CREDENTIAL_PLACEHOLDER>
>>> dotnet dev-certs https --trust
>>> ```  
>>> 在上述命令中，将 <CREDENTIAL_PLACEHOLDER> 替换为密码。
>>> 在命令行界面中使用配置了 HTTPS 的 ASP.NET Core 运行容器映像：  
>>> ```cmd
>>> docker pull mcr.microsoft.com/dotnet/samples:aspnetapp`
>>> docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORTS=8001 -e ASPNETCORE_Kestrel__Certificates__Default__Password="<CREDENTIAL_PLACEHOLDER>" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/aspnetapp.pfx -v %USERPROFILE%\.aspnet\https:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
>>> ```  
>>> 在上述代码中，将 <CREDENTIAL_PLACEHOLDER> 替换为密码。 密码必须与证书所用的密码一致。  
>>> 使用 PowerShell 时，将 %USERPROFILE% 替换为 $env:USERPROFILE。  
>>> 注意1：本示例中的证书必须是 .pfx 文件。 示例容器不支持使用带或不带密码的 .crt 或 .key 文件。 例如，指定 .crt 文件时，容器可能会返回错误消息，例如“服务器模式 SSL 必须使用具有关联私钥的证书”。 使用 WSL 时，请验证装载路径以确保正确加载证书
>>> 注意2：本实例中容器镜像替换为实际使用中的镜像。



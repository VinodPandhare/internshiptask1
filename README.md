<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>

  <p align="center">A progressive <a href="http://nodejs.org" target="blank">Node.js</a> framework for building efficient and scalable server-side applications, heavily inspired by <a href="https://angular.io" target="blank">Angular</a>.</p>
  
</p>

 # HERE IS THE WHICH IS USED FOR THIS TASK
```
# Set the path to the security key & Replace it with your KeyPair Name 
$path = "C:\Users\HP\Downloads\Security_key.pem"

# Reset the permissions of the file
icacls.exe $path /reset

# Grant read permissions to the current user
$username = $env:USERNAME
icacls.exe $path /GRANT:R "${username}:(R)"

Write-Host "Permissions set successfully for $path"

```


# dev-ops-daily-practices

Powershell Command to send mail using Azure ACS SMTP Relay
    
    $Password = ConvertTo-SecureString -AsPlainText -Force -String 'your-smtp-password'
    $Cred = New-Object -TypeName PSCredential -ArgumentList 'ur-smtp-username@azurecomm.net', $Password
    
    Send-MailMessage -From 'your-smtp-username@azurecomm.net' `
    -To 'sivasankar.thalavai@gmail.com' `
    -Subject 'Test mail' `
    -Body 'test' `
    -SmtpServer 'smtp.office365.com' `
    -Port 587 `
    -Credential $Cred `
    -UseSsl


=====================================================================

Bash Shell Command to send mail using Azure ACS SMTP Relay

    sudo apt install swaks
    
    swaks --to sivasankar.thalavai@marlabs.com \
      --from your-smtp-username@azurecomm.net \
      --server smtp.office365.com \
      --port 587 \
      --auth LOGIN \
      --auth-user your-smtp-username@azurecomm.net \
      --auth-password 'your-smtp-password' \
      --tls \
      --header "Subject: Test mail" \
      --body "test"
  

=====================================================================

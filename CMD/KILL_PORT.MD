`for /f "tokens=5" %a in ('netstat -ano ^| findstr :<PortNumber>') do taskkill /pid %a /f`

Example:
`for /f "tokens=5" %a in ('netstat -ano ^| findstr :8080') do taskkill /pid %a /f`

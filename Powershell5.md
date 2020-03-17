#Taller 5
#Ejercicios:
1.	¿Cuál clase puede emplearse para consultar la dirección IP de un adaptador de red? ¿Posee dicha clase algún método para liberar un préstamo de dirección (lease) DHCP?

Respuesta:

``Get-CimInstance -Class Win32_NetworkAdapterConfiguration | select IP, ServiceName``

La clase  Win32_NetworkAdapterConfiguration no posee algún método que libere un préstamo en dirección DHCP.


2.	Despliegue una lista de parches empleando WMI (Microsoft se refiere a los parches con el nombre quick-fix engineering). Es diferente el listado al que produce el cmdlet Get-Hotfix?

Respuesta:

``Get-WmiObject win32_QuickFixEngineering``

3.	Empleando WMI, muestre una lista de servicios, que incluya su status actual, su modalidad de inicio, y las cuentas que emplean para hacer login.

Respuesta:

``Get-WmiObject win32_service | Select-Object status, startmode, systemname``

4.	Empleando cmdlets de CIM, liste todas las clases del namespace SecurityCenter2, que tengan product como parte del nombre.

Respuesta:

``Get-CimClass -Namespace root/SecurityCenter2 | where CimClassName -Like '*product*'``

5.	Empleando cmdlets de CIM, y los resultados del ejercicio anterior, muestre los nombres de las aplicaciones antispyware instaladas en el sistema. También puede consultar si hay productos antivirus instalados en el sistema.

Respuesta:

``Get-CimClass -Namespace root\SecurityCenter2 | where cimclassname -Like 'spyware'``

``Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntiVirusProduct ``

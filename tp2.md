# Atelier n° 2

**SUJET**</br>

Création de l’arborescence Active Directory sur du papier, nous essaierons d’automatiser les créations des OU.  
Pour chacun des services créez 30 utilisateurs : 2 responsable RD pour le Responsable Direction   
Nous utiliserons un script PowerShell fournit pour les noms des utilisateurs.  

Modifier les propriétés de comptes afin que les employés ne puissent pas changer leur mot de passe.   
Seuls les responsables ont l’autorisation de se connecter le week-end.  
Renseigner pour tous les utilisateurs les champs Villes, Fonction, Service et Société.  
Créez un Serveur Membre à partir de la Base Windows Server 2019 dans chaque Site Paris, Marseille et Lyon et placez-les dans leurs UO Serveur respective. Nommez-les en respectant</br> la convention suivante : SMM1 pour le premier Serveur Membre du site de  Marseille. Le site Lyon compte deux serveurs Membres.
Créez un Serveur Membre Core à partir de la Base Windows Server 2019 Core dans le site de Paris, placez-le dans son UO Serveur respective. Nommez-le en respectant la convention</br> suivante : SMCP1 pour le premier Serveur Membre Core de Paris. 
Créer un client par site géographiques.


pour OU, Si y a que utilisateur ou ordi conditions pas respecter; toujours remplir description pour simplifier lecteru erreurs; créer utlisateur virtuelle qui supervise :supervision 
regarder bien quand coche pour new object + dans propriete y a plein de chose à remplir
automatiser remplissage car si plein de truc a remp peut se tromper; on gere plein de truc avec le script
gérer en entrée , se mettre d'accord sur le filtrage comme ça on sais ou aller pour corriger
On peut changer la destination du profil, il peut avoir son profil sur sa clé gentre U:profile et dés que la clé se monte il a son profil.
si a systeme gpo si ajoute un membre y a des ruc mis en auto/remp selon regle


pour retirer droit sur un dossier si a pas décocher pour OU: views -> advances feature -> dossier-> properties

**1: faire arboresccences des utilisateur et ordi (OU)**</br>
Modifier au final on a Sites(lyon,paris,marseille) ou dedans on a service et computer comme dossier, et dans services on a Direction, Informatique, Compta, Marketing, Production 
Utilisateur:
  - Lyon(OU)
        - Direction
        - Informatique
        - Compta
        - Marketing
        - Production
  - Paris(OU)
        - Direction
        - Informatique
        - Compta
        - Marketing
        - Production
  - Marseille(OU)
        - Direction
        - Informatique
        - Compta
        - Marketing
        - Production </br>

**2:Script pour faire cette arbo**  # script doit etre fini pour atelier 3( février) </br>
on tape power dans vm-CD (power Shell ISE à choisir)
New-ADOrganizationalUnit -Name "Lyon" -Path "OU=UTILISATEURS,DC=ENS,DC=dom"   (pour créer OU lyon) MAIS avant il faut faire les vyos

```function New-Password'
{

'$Alphabets = 'a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z'
$numbers = 0..9
$specialCharacters = '~,!,@,#,$,%,^,&,*,(,),>,<,?,\,/,_,-,=,+'
$array = @()
$array += $Alphabets.Split(',') | Get-Random -Count 4
$array[0] = $array[0].ToUpper()
$array[-1] = $array[-1].ToUpper()
$array += $numbers | Get-Random -Count 3
$array += $specialCharacters.Split(',') | Get-Random -Count 3
($array | Get-Random -Count $array.Count) -join ""
}


#########
function New-RandomUser {
    <#
    .SYNOPSIS
    Generate random user data from Https://randomuser.me/.
    .DESCRIPTION
    This function uses the free API for generating random user data from https://randomuser.me/
    .EXAMPLE
    Get-RandomUser 10
    .EXAMPLE
    Get-RandomUser -Amount 25 -Nationality us,gb 
    .LINK
    https://randomuser.me/
    #>
    [CmdletBinding()]
    param (
    [Parameter(Position = 0)]
    [ValidateRange(1,500)]
    [int] $Amount,
    
    [Parameter()]
    [ValidateSet('Male','Female')]
    [string] $Gender,
    
    # Supported nationalities: AU, BR, CA, CH, DE, DK, ES, FI, FR, GB, IE, IR, NL, NZ, TR, US
    [Parameter()]
    [string[]] $Nationality,
    
    
    [Parameter()]
    [ValidateSet('json','csv','xml')]
    [string] $Format = 'json',
    
    # Fields to include in the results.
    # Supported values: gender, name, location, email, login, registered, dob, phone, cell, id, picture, nat
    [Parameter()]
    [string[]] $IncludeFields,
    
    # Fields to exclude from the the results.
    # Supported values: gender, name, location, email, login, registered, dob, phone, cell, id, picture, nat
    [Parameter()]
    [string[]] $ExcludeFields
    )
    
    $rootUrl = "http://api.randomuser.me/?format=$($Format)"
    
    if ($Amount) {
    $rootUrl += "&results=$($Amount)"
    }
    
    if ($Gender) {
    $rootUrl += "&gender=$($Gender)"
    }
    
    
    if ($Nationality) {
    $rootUrl += "&nat=$($Nationality -join ',')"
    }
    
    if ($IncludeFields) {
    $rootUrl += "&inc=$($IncludeFields -join ',')"
    }
    
    if ($ExcludeFields) {
    $rootUrl += "&exc=$($ExcludeFields -join ',')"
    }
    
    Invoke-RestMethod -Uri $rootUrl
    }

   $tt= New-RandomUser -Amount 30 -Nationality FR -IncludeFields name,phone,cell -ExcludeFields picture | Select-Object -ExpandProperty results
##############

# recup le dommain   (surligner une variable et faire f8)+(f5 pour run script
$doma =Get-ADDomain
$domain=($doma.DNSROOT).split('.')
$Dom = $domain[0]
$ext =$domain[1]

#OU sites
New-ADOrganizationalUnit -Name "Sites" -Path "DC=$Dom,DC=$ext"  -ProtectedFromAccidentalDeletion $false # sert a decocher droit pour pouvoir delete le ou 

$tablCity = @("Lyon","Paris","Marseille") 
$tabService=@("direction","marketing","informatique","compatbilite","production")

foreach ($city in $tablCity){
        New-ADOrganizationalUnit -Name $city -Path "OU=Sites,DC=$Dom,DC=$ext"  -ProtectedFromAccidentalDeletion $false 
        New-ADOrganizationalUnit -Name "computer" -Path "OU=$city,OU=Sites,DC=$Dom,DC=$ext"  -ProtectedFromAccidentalDeletion $false 
        New-ADOrganizationalUnit -Name "service" -Path "OU=$city,OU=Sites,DC=$Dom,DC=$ext"  -ProtectedFromAccidentalDeletion $false 
        $i=0;
    foreach ($service in $tabService){
         New-ADOrganizationalUnit -Name $service -Path "OU=service,OU=$city, OU=Sites,DC=$Dom,DC=$ext"  -ProtectedFromAccidentalDeletion $false 
         $users= New-RandomUser -Amount 30 -Nationality FR -IncludeFields name,phone,cell -ExcludeFields picture | Select-Object -ExpandProperty results 
         $resp = 0
        foreach($user in $users){
            $title = "EMP"
            $changePassword = $true
            if($resp -lt 2){
                $title = "RD"
                $changePassword = $false
                $resp++
            }
           New-ADUser -Name ($user.name.first+'.'+$user.name.last) -DisplayName ($user.name.last+" "+$user.name.first) -HomePhone $user.phone -MobilePhone $user.cell 
 -GivenName $user.name.first   -Surname $user.name.last  -Title $title  -Company ($Dom+""+ $site)  -City $site -CannotChangePassword $changePassword  -Path "OU =$service, OU =service,OU=$city, OU=Sites,DC=$Dom,DC=$ext"
           #condition que les responsables ne peuvent pas se co le WE
           if($title -eq "EMP"){
           [byte[]]$hours = @(0,0,0,0,255,3,0,255,3,0,255,3,0,255,3,0,255,3,0,0,0)
           Get-ADUser -Identity ($user.name.first+'.'+$user.name.last) | Set-ADUser -Replace @{logonhours=$hours}
           }

         }
    } 
 
      
    }

    Get-ADUser -Filter 'Title -like "RD" 
```







**2,5 : VyOS (routeur virtuelle):** </br>
importe vm vyos(snapshot+clone)  (login: vyos   mdp: vyos )
pour mettre en fr : set console keymap -> generique 105 -> other -> french-> french -> ok->ok

ajouter en physic (settings-> add ->W network adaptater)  les interfaces

cf schéma claire (photo) sur vmnet2 mettre ip passerelle   + https://www.tutos.snatch-crash.fr/vyos-routeur-virtuel/ 
vmnet3 tous les sites lié a lui

=>/29 pour les inter-routeur:
  Lyon (1)-Marseille(2)- Paris(3): 1.1.1.x

---------------------------------------------------------------LYON------------------------------------------------------------------------------------
Pour mettre du vmnet2 sut du eth1 on fait dans les settings de la vm  </br>
show interface  </br>
configure  </br>
set interfaces ethernet eth2 address dhcp (dhcp c'est pour internet) </br>
Pour mettre du vmnet3 sut du eth3(4e adaptateur) on fait dans les settings de la vm </br>
Puis on doit mettre la inrerouteur sur vmnet3 car c'est la que tout connecté </br>
set interfaces ethernet eth1 address 172.31.1.254/16   (passerrel vers réseau) </br>
set interfaces ethernet eth3 address 1.1.1.1/29  </br>

eth10->vmnet2  eth11->vmnet3   eth9->dhcp</br>

Pour savoir le num adaptateur on peut show int quand on déco un adataptateur en bas à droite.</br>

 commit +save pour save les modif    si veut enlever qql chose faire delete devant commande </b>
 
 ---------------------------------------------------------------Marseille---------------------------------------------------------------------------------------
Pour mettre du vmnet2 sut du eth1 on fait dans les settings de la vm </br>
Pour mettre du vmnet3 sut du eth2 on fait dans les settings de la vm </br>
show interface </br>
configure </br>
Puis on doit mettre l'ip inrerouteur sur vmnet3 car c'est la que tout connecté </br>
set interfaces ethernet eth2 address 1.1.1.2/29   </br>
set interfaces ethernet eth1 address 172.31.1.254/16   (passerrel vers réseau privé)  </br>

eth7->vmnet2   eth4->vmnet3 </br>

 commit +save pour save les modif    si veut enlever qql chose faire delete devant commande</b>
 
  ---------------------------------------------------------------Paris------------------------------------------------------------------------------------------
Pour mettre du vmnet2 sut du eth1 on fait dans les settings de la vm </br>
Pour mettre du vmnet3 sut du eth2 on fait dans les settings de la vm </br>
show interface </br>
configure </br>
Puis on doit mettre l'ip inrerouteur sur vmnet3 car c'est la que tout connecté </br>
set interfaces ethernet eth2 address 1.1.1.3/29   </br>
set interfaces ethernet eth1 address 172.31.1.254/16   (passerrel vers réseau privé) </br>

eth6->vmnet2   eth7->vmnet3 </br>

commit +save pour save les modif    si veut enlever qql chose faire delete devant commande</b>

---------------------------------------------------------------------------------------------------------------------------------------------------------------

 
Important doit avoir le vyos vm allumer avec serveur car sinon peut pas ping (normal c'est le routeur)
https://www.tech2tech.fr/installation-dun-routeur-virtuel-leger-avec-vyos/ 

**rip** </br>
Om met du rip car on a 3 routeurs :
configure
 set protocols rip interface <interface>(eth*=> celle qui ont vmnet3)
Pour enlever les firewall de Paris(Core) 
  netsh advfirewall set domainprofil state off
  netsh advfirewall set privateprofil state off 
  netsh advfirewall set publicprofil state off.

**Serveur membre** </br>
cloner pour avoir 2 serveur memebre pour lyon et 1 pour les 2 autre (pour paris c'est un core)
Potentiellement changer addressage car potentiellement dans la merde
Penser a les mettre en vmnet2
Enlever les firewall
Il faut bien penser a mettre addresse dns + gateway
(Si parfois pas internet c'est peut etre carte réseau qui est déco) 

SMlyon1-> 172.31.1.4 </br>
SMLyon2->172.31.1.5 </br>
SMMarseille->172.31.1.6 </br>
SMParis->172.31.1.7 </br>   -> netsh interface ipv4 set address name=Ethernet0 static 172.31.1.7 255.255.0.0 172.31.1.254 -> netdom join SMP1 /domain :ESN.dom /ud :Administrator /pd :123+aze

**pb les serveur memebre pin pas 8.8.8.8 (mais pinf bin cd lyon)**

**Client** </br>
https://www.microsoft.com/fr-fr/software-download/windows10
del le windows puis faire une vm avec l'iso de windoms , lancer puis installé windoms </br>
Rep au question de sécu + user : Administrator  </br>  
(compte hors connexion + c'est un perso / pas entreprise)</br>
clientLyon -> 172.31.1.8  (user : Michel)</br>
clientParis -> 172.31.1.9 </br>
clientMarseille -> 172.31.1.10 </br>

Pour faire rejoindre ens : windom+r -> sysdm.cpl puis modifier et on nomme le pc puis on selectionne le domaine ENS.dom (attention parfois faut s'amuser avec les réseau car sinon fonctionne pas)


DNAT (nat en entrée)

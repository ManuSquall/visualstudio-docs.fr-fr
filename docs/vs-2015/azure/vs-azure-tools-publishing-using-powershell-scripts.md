---
title: À l’aide de Scripts de Windows PowerShell pour publier dans les environnements de Test et de développement | Microsoft Docs
description: Découvrez comment utiliser des scripts Windows PowerShell à partir de Visual Studio pour publier de développement et environnements de test.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001874"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Utilisation de scripts Windows PowerShell pour publier sur des environnements de développement et de test

Lorsque vous créez une application web dans Visual Studio, vous pouvez générer un script Windows PowerShell que vous pouvez utiliser ultérieurement pour automatiser la publication de votre site Web vers Azure en tant qu’une application Web dans Azure App Service ou une machine virtuelle. Vous pouvez modifier et étendre le script Windows PowerShell dans l’éditeur Visual Studio pour répondre à vos besoins ou intégrer ce script de build existante, de test et de scripts de publication.

À l’aide de ces scripts, vous pouvez configurer des versions personnalisées (également connu sous les environnements de développement et de test) de votre site pour une utilisation temporaire. Par exemple, vous pouvez configurer une version particulière de votre site Web sur une machine virtuelle Azure ou sur l’emplacement intermédiaire sur un site Web pour exécuter une suite de tests, reproduire un bogue, tester un correctif, évaluer une proposition de modification ou configurer un environnement personnalisé pour une démonstration ou une présentation. Une fois que vous avez créé un script qui publie votre projet, vous pouvez recréer des environnements identiques en réexécutant le script en fonction des besoins, ou exécutez le script avec votre propre build de votre application web pour créer un environnement personnalisé pour le test.

## <a name="prerequisites"></a>Prérequis

* Azure SDK 2.3 ou version ultérieure. Consultez [téléchargements Visual Studio](http://go.microsoft.com/fwlink/?LinkID=624384). (Vous n’avez pas besoin du Kit de développement pour générer les scripts pour les projets web. Cette fonctionnalité est pour les projets web, pas les rôles web dans les services cloud.)
* Azure PowerShell 0.7.4 ou une version ultérieure. Consultez [comment installer et configurer Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) ou version ultérieure.

## <a name="additional-tools"></a>Outils supplémentaires

Autres outils et ressources pour l’utilisation de PowerShell dans Visual Studio pour le développement Azure sont disponibles. Consultez [PowerShell Tools pour Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Génération de scripts de publication

Vous pouvez générer des scripts de publication pour une machine virtuelle qui héberge votre site Web lorsque vous créez un nouveau projet en suivant [ces instructions](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Vous pouvez également [générer des scripts de publication pour les applications web dans Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Scripts générés par Visual Studio

Visual Studio génère un dossier de niveau solution appelé **PublishScripts** qui contient deux fichiers de Windows PowerShell, un script de publication pour votre machine virtuelle ou site Web et un module qui contient les fonctions que vous pouvez utiliser dans le scripts. Visual Studio génère également un fichier au format JSON qui spécifie les détails du projet que vous déployez.

### <a name="windows-powershell-publish-script"></a>Script de publication de Windows PowerShell

Le script de publication contient des étapes de publication spécifiques pour le déploiement sur un site Web ou d’une machine virtuelle. Visual Studio fournit les couleurs de syntaxe pour le développement de Windows PowerShell. L’aide pour les fonctions n’est disponible, et vous pouvez modifier librement les fonctions dans le script en fonction de vos besoins.

### <a name="windows-powershell-module"></a>Module Windows PowerShell

Le module Windows PowerShell généré par Visual Studio contient des fonctions qui utilise le script de publication. Ces fonctions Azure PowerShell ne sont pas destinées à être modifiées. Consultez [comment installer et configurer Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Fichier de configuration JSON

Le fichier JSON est créé dans le **Configurations** dossier et contient les données de configuration qui spécifie exactement les ressources à déployer dans Azure. Le nom du fichier généré par Visual Studio est projet-nom-WAWS-dev.JSON si vous avez créé un site Web ou un projet nom-VM-dev.JSON si vous avez créé une machine virtuelle. Voici un exemple de fichier de configuration JSON généré lorsque vous créez un site Web. La plupart des valeurs est explicite. Le nom du site Web est généré par Azure, il peut ne pas correspondre à votre nom de projet.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Lorsque vous créez une machine virtuelle, le fichier de configuration JSON ressemble à ce qui suit. Un service cloud est créé en tant que conteneur pour la machine virtuelle. La machine virtuelle contient les points de terminaison habituels pour l’accès web via HTTP et HTTPS, ainsi que les points de terminaison pour Web Deploy, qui vous permet de publier sur le site Web à partir de votre ordinateur local, le Bureau à distance et Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Vous pouvez modifier la configuration JSON pour modifier ce qui se passe lorsque vous exécutez des scripts de publication. Le `cloudService` et `virtualMachine` sections sont requises, mais vous pouvez supprimer le `databases` section si vous n’avez pas besoin. Les propriétés qui sont vides dans le fichier de configuration par défaut généré par Visual Studio sont facultatives ; Ces propriétés qui ont des valeurs dans le fichier de configuration par défaut sont requises.

Si vous avez un site Web qui a plusieurs environnements de déploiement (appelés emplacements) au lieu d’un site de production unique dans Azure, vous pouvez inclure le nom de l’emplacement dans le nom du site Web dans le fichier de configuration JSON. Par exemple, si vous avez un site Web nommé **monsite** et son emplacement est nommé **tester** , l’URI est `mysite-test.cloudapp.net`, mais le nom correct à utiliser dans le fichier de configuration est monsite (test). Vous ne pouvez le faire ceci si le site Web et emplacements existent déjà dans votre abonnement. Si elles n’existent pas, créez le site Web en exécutant le script sans spécifier l’emplacement, puis créez l’emplacement dans le [Azure portal](https://portal.azure.com/), ensuite, exécutez le script avec le nom de site Web modifié. Pour plus d’informations sur les emplacements de déploiement pour les applications web, consultez [définir des environnements intermédiaires pour applications web dans Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Comment exécuter des scripts de publication

Si vous n’avez jamais exécuté un script Windows PowerShell avant, vous devez d’abord définir la stratégie d’exécution pour activer les scripts à exécuter. La stratégie est une fonctionnalité de sécurité pour empêcher les utilisateurs d’exécuter des scripts Windows PowerShell s’ils sont vulnérables aux programmes malveillants ou virus impliquant l’exécution de scripts.

### <a name="run-the-script"></a>Exécutez le script

1. Créez le package Web Deploy pour votre projet. Un package Web Deploy est une archive compressée (fichier .zip) qui contiennent les fichiers que vous souhaitez copier sur votre site Web ou d’une machine virtuelle. Vous pouvez créer des packages Web Deploy dans Visual Studio pour n’importe quelle application web.

   ![Créer Web déployer le Package](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Pour plus d’informations, consultez [Comment : créer un Package de déploiement Web dans Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Vous pouvez également automatiser la création de votre package Web Deploy, comme décrit dans [personnalisation et extension des scripts de publication](#customizing-and-extending-publish-scripts).

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le script, puis choisissez **ouvrir avec PowerShell ISE**.
1. Si vous exécutez des scripts Windows PowerShell sur cet ordinateur pour la première fois, ouvrez une fenêtre d’invite de commandes avec des privilèges d’administrateur et tapez la commande suivante :

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Connectez-vous à Azure à l’aide de la commande suivante.

    ```powershell
    Add-AzureAccount
    ```

    Lorsque vous y êtes invité, fournissez votre nom d’utilisateur et le mot de passe.

    Notez que lorsque vous automatisez le script, cette méthode de renseignement des informations d’identification Azure ne fonctionne pas. Au lieu de cela, vous devez utiliser le `.publishsettings` fichier pour fournir des informations d’identification. Une fois seulement, vous utilisez la commande **Get-AzurePublishSettingsFile** pour télécharger le fichier à partir d’Azure et par la suite utiliser **Import-AzurePublishSettingsFile** pour importer le fichier. Pour obtenir des instructions détaillées, consultez [comment installer et configurer Azure PowerShell](/powershell/azure/overview).

1. (Facultatif) Si vous souhaitez créer des ressources Azure telles que la machine virtuelle, base de données et le site Web sans avoir à publier votre application web, utilisent le **Publish-WebApplication.ps1** commande avec le **-Configuration**argument défini au fichier de configuration JSON. Cette ligne de commande utilise le fichier de configuration JSON pour déterminer les ressources à créer. Car elle utilise les paramètres par défaut pour les autres arguments de ligne de commande, il crée les ressources, mais ne publie pas votre application web. – Verbose option vous donne plus d’informations sur ce qui se passe.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Utilisez le **Publish-WebApplication.ps1** commande comme indiqué dans un des exemples suivants pour appeler le script et publier votre application web. Si vous devez remplacer les paramètres par défaut pour tous les autres arguments, telles que le nom de l’abonnement, nom du package, les informations d’identification de la machine virtuelle ou les informations d’identification du serveur de base de données de publication, vous pouvez spécifier ces paramètres. Utilisez le **– Verbose** option afin d’afficher plus d’informations sur la progression du processus de publication.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Si vous créez une machine virtuelle, la commande se présente comme suit. Cet exemple montre également comment spécifier les informations d’identification pour plusieurs bases de données. Pour les machines virtuelles créées par ces scripts, le certificat SSL n’est pas à partir d’une autorité racine approuvée. Par conséquent, vous devez utiliser le **– AllowUntrusted** option.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Le script peut créer des bases de données, mais il ne crée pas de serveurs de base de données. Si vous souhaitez créer un serveur de base de données, vous pouvez utiliser la **New-AzureSqlDatabaseServer** dans le module Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Personnalisation et extension des scripts de publication

Vous pouvez personnaliser le script de publication et le fichier de configuration JSON. Les fonctions dans le module Windows PowerShell **AzureWebAppPublishModule.psm1** ne sont pas destinées à être modifiées. Si vous souhaitez simplement spécifier une autre base de données ou modifier certaines des propriétés de la machine virtuelle, modifiez le fichier de configuration JSON. Si vous souhaitez étendre les fonctionnalités du script afin d’automatiser la création et de test de votre projet, vous pouvez implémenter les stubs de fonction dans **Publish-WebApplication.ps1**.

Pour automatiser la création de votre projet, ajoutez le code appelant MSBuild à `New-WebDeployPackage` comme indiqué dans cet exemple de code. Le chemin d’accès à la commande MSBuild est différent selon la version de Visual Studio que vous avez installée. Pour obtenir le chemin d’accès correct, vous pouvez utiliser la fonction **Get-MSBuildCmd**, comme illustré dans cet exemple.

### <a name="to-automate-building-your-project"></a>Pour automatiser la création de votre projet

1. Ajouter le `$ProjectFile` paramètre dans la section des paramètres globaux.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copiez la fonction `Get-MSBuildCmd` dans votre fichier de script.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Remplacez `New-WebDeployPackage` avec le code suivant et remplacez les espaces réservés dans la ligne créant `$msbuildCmd`. Ce code est pour Visual Studio 2015. Si vous utilisez Visual Studio 2017, modifiez le **VisualStudioVersion** propriété `15.0` (`12.0` pour Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Pour générer votre application web, utilisez MsBuild.exe. Pour obtenir, consultez la référence de ligne de commande MSBuild : [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Démarrer l’exécution de la commande de build

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Appelez le `New-WebDeployPackage` (fonction) avant cette ligne : `$Config = Read-ConfigFile $Configuration` pour les applications web ou `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` pour les machines virtuelles.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Appelez le script personnalisé à partir de la ligne de commande à l’aide de la transmission du `$Project` argument, comme dans l’exemple suivant :

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Pour automatiser le test de votre application, ajoutez le code à `Test-WebApplication`. Veillez à ne pas commenter les lignes dans **Publish-WebApplication.ps1** dans lesquelles ces fonctions sont appelées. Si vous ne fournissez pas d’implémentation, vous pouvez créer manuellement votre projet avec Visual Studio et puis exécutez le script de publication pour publier sur Azure.

## <a name="publishing-function-summary"></a>Résumé de la fonction publication
Pour obtenir une aide pour les fonctions que vous pouvez utiliser à l’invite de commande Windows PowerShell, utilisez la commande `Get-Help function-name`. L’aide contient des exemples et l’aide du paramètre. Le même texte d’aide est également dans les fichiers de sources de script **AzureWebAppPublishModule.psm1** et **Publish-WebApplication.ps1**. Le script et aide est localisée dans votre langage de Visual Studio.

**AzureWebAppPublishModule**

| Nom de la fonction | Description |
| --- | --- |
| Add-AzureSQLDatabase |Crée une nouvelle base de données SQL Azure. |
| Add-AzureSQLDatabases |Crée des bases de données SQL Azure à partir des valeurs dans le fichier de configuration JSON généré par Visual Studio. |
| Add-AzureVM |Crée une machine virtuelle Azure et renvoie l’URL de la machine virtuelle déployée. Cette fonction configure les conditions préalables, puis appelle la **New-AzureVM** (fonction) (module Azure) pour créer une machine virtuelle. |
| Add-AzureVMEndpoints |Ajoute de nouveaux points de terminaison d’entrée à une machine virtuelle et renvoie la machine virtuelle avec le nouveau point de terminaison. |
| Add-AzureVMStorage |Crée un nouveau compte de stockage Azure dans l’abonnement actuel. Le nom du compte commence par « devtest » suivie d’une chaîne alphanumérique unique. La fonction retourne le nom du nouveau compte de stockage. Spécifiez un emplacement ou un groupe d’affinités pour le nouveau compte de stockage. |
| Add-AzureWebsite |Crée un site Web avec le nom spécifié et l’emplacement. Cette fonction appelle le **New-AzureWebsite** dans le module Azure. Si l’abonnement ne contient pas déjà un site Web avec le nom spécifié, cette fonction crée le site Web et retourne un objet de site Web. Sinon, il retourne `$null`. |
| Backup-Subscription |Enregistre l’abonnement Azure actif dans le `$Script:originalSubscription` variable dans la portée de script. Cette fonction enregistre l’abonnement Azure actuel (tel qu’obtenu par `Get-AzureSubscription -Current`) et son compte de stockage et l’abonnement est modifié par ce script (stocké dans la variable `$UserSpecifiedSubscription`) et son compte de stockage, dans la portée de script. En enregistrant les valeurs, vous pouvez utiliser une fonction, tel que `Restore-Subscription`, pour restaurer le compte de stockage et d’abonnement en cours d’origine de l’état actuel, si l’état actuel a changé. |
| Find-AzureVM |Obtient la machine virtuelle Azure spécifiée. |
| Format-DevTestMessageWithTime |Ajoute la date et l’heure à un message. Cette fonction est conçue pour les messages écrits dans les flux Error et Verbose. |
| Get-AzureSQLDatabaseConnectionString |Assemble une chaîne de connexion pour se connecter à une base de données SQL Azure. |
| Get-AzureVMStorage |Retourne le nom du premier compte de stockage avec le modèle de nom « devtest *» (la casse) dans l’emplacement spécifié ou le groupe d’affinités. Si le « devtest*« compte de stockage ne correspond pas à l’emplacement ou le groupe d’affinités, la fonction l’ignore. Spécifiez un emplacement ou un groupe d’affinités. |
| Get-MSDeployCmd |Retourne une commande pour exécuter l’outil MsDeploy.exe. |
| New-AzureVMEnvironment |Recherche ou crée une machine virtuelle dans l’abonnement qui correspond aux valeurs dans le fichier de configuration JSON. |
| Publish-WebPackage |Utilise MsDeploy.exe et un site web publient le package. Fichier ZIP pour déployer des ressources à un site Web. Cette fonction ne génère aucune sortie. Si l’appel de MSDeploy.exe échoue, la fonction lève une exception. Pour obtenir une sortie plus détaillée, utilisez le **-Verbose** option. |
| Publish-WebPackageToVM |Vérifie les valeurs de paramètre et appelle ensuite la **Publish-WebPackage** (fonction). |
| Read-ConfigFile |Valide le fichier de configuration JSON et retourne une table de hachage des valeurs sélectionnées. |
| Restore-Subscription |Réinitialise l’abonnement actuel à l’abonnement d’origine. |
| Test-AzureModule |Retourne `$true` si la version du module Azure installé est 0.7.4 ou une version ultérieure. Retourne `$false` si le module n’est pas installé ou est une version antérieure. Cette fonction n’a aucun paramètre. |
| Test-AzureModuleVersion |Retourne `$true` si la version du module Azure est 0.7.4 ou une version ultérieure. Retourne `$false` si le module n’est pas installé ou est une version antérieure. Cette fonction n’a aucun paramètre. |
| Test-HttpsUrl |Convertit l’URL d’entrée à un objet System.Uri. Retourne `$True` si l’URL est absolue et son schéma est https. Retourne `$false` si l’URL est relative, son schéma n’est pas HTTPS ou la chaîne d’entrée ne peut pas être convertie en URL. |
| Membre de test |Retourne `$true` si une propriété ou méthode est un membre de l’objet. Sinon, retourne `$false`. |
| ErrorWithTime d’écriture |Écrit un message d’erreur préfixé avec l’heure actuelle. Cette fonction appelle le **Format-DevTestMessageWithTime** (fonction) pour ajouter l’heure avant d’écrire le message dans le flux d’erreurs. |
| HostWithTime d’écriture |Écrit un message dans le programme hôte (**Write-Host**) préfixé avec l’heure actuelle. L’effet de l’écriture dans le programme hôte varie. La plupart des programmes qui hébergent Windows PowerShell écrire ces messages vers la sortie standard. |
| VerboseWithTime d’écriture |Écrit un message détaillé préfixé avec l’heure actuelle. Étant donné qu’il appelle **Write-Verbose**, le message s’affiche uniquement lorsque le script est exécuté avec le **Verbose** paramètre ou lorsque le **VerbosePreference** préférence est définie sur  **Continuer**. |

**Application Web de publication**

| Nom de la fonction | Description |
| --- | --- |
| Nouvelle AzureWebApplicationEnvironment |Crée des ressources Azure, tel qu’un site Web ou d’une machine virtuelle. |
| Nouvelle WebDeployPackage |Cette fonction n’est pas implémentée. Vous pouvez ajouter des commandes à cette fonction pour générer votre projet. |
| AzureWebApplication publier |Publie une application web vers Azure. |
| Application Web de publication |Crée et déploie des applications Web, les machines virtuelles, les bases de données SQL et les comptes de stockage pour un projet web Visual Studio. |
| Test-WebApplication |Cette fonction n’est pas implémentée. Vous pouvez ajouter des commandes à cette fonction pour tester votre application. |

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur l’écriture de scripts PowerShell en lisant [écriture de scripts avec Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) et consultez les autres scripts Azure PowerShell sur le [centre de scripts](https://azure.microsoft.com/documentation/scripts/).

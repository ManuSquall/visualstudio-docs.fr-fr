---
title: "How to: Configure the ClickOnce Trust Prompt Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, install without prompting"
  - "deploying applications [ClickOnce], trust prompt"
  - "ClickOnce applications, install without prompting"
  - "ClickOnce applications, trust prompt"
  - "ClickOnce deployment, trust prompt"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Configure the ClickOnce Trust Prompt Behavior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez configurer l'invite d'approbation ClickOnce pour contrôler si les utilisateurs finaux peuvent installer des applications ClickOnce, telles que les applications Windows Forms, les applications Windows Presentation Foundation, les applications console, les applications de navigateur WPF et les solutions Office.  Vous configurez l'invite d'approbation en définissant des clés de Registre sur l'ordinateur de chaque utilisateur final.  
  
 Le tableau suivant affiche les options de configuration qui peuvent être appliquées à chacune des cinq zones \(Internet, UntrustedSites, MyComputer, LocalIntranet et TrustedSites\).  
  
|Option|Valeur du paramètre du Registre|Description|  
|------------|-------------------------------------|-----------------|  
|Activer l'invite d'approbation.|`Activé`|L'invite d'approbation ClickOnce s'affiche afin que les utilisateurs finaux puissent approuver les applications ClickOnce.|  
|Restreindre l'invite d'approbation.|`AuthenticodeRequired`|L'invite d'approbation ClickOnce s'affiche uniquement si les applications ClickOnce sont signées avec un certificat qui identifie l'éditeur.|  
|Désactiver l'invite d'approbation.|`Disabled`|L'invite d'approbation ClickOnce ne s'affiche pas pour les applications ClickOnce qui ne sont pas signées avec un certificat explicitement approuvé.|  
  
 Le tableau suivant indique le comportement par défaut pour chaque zone.  La colonne Applications fait référence aux applications Windows Forms, aux applications Windows Presentation Foundation, aux applications de navigateur WPF et aux applications console.  
  
|Zone|Applications|solutions Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Activé`|`Activé`|  
|`LocalIntranet`|`Activé`|`Activé`|  
|`TrustedSites`|`Activé`|`Activé`|  
|`Internet`|`Activé`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Vous pouvez substituer ces paramètres en activant, restreignant ou désactivant l'invite d'approbation ClickOnce.  
  
## Activation de l'invite d'approbation ClickOnce  
 Activez l'invite d'approbation pour une zone si vous voulez que les utilisateurs finaux aient la possibilité d'installer et d'exécuter les applications ClickOnce provenant de cette zone.  
  
#### Pour activer l'invite d'approbation ClickOnce à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez `regedit32`, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si cette clé n'existe pas, créez\-la.  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées présentées dans le tableau suivant.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |`Internet`|`Activé`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Activé`|  
    |`LocalIntranet`|`Activé`|  
    |`TrustedSites`|`Activé`|  
  
     Pour les solutions Office, `Internet` a par défaut la valeur `AuthenticodeRequired` et `UntrustedSites` a la valeur `Disabled`.  Pour toutes les autres solutions, `Internet` a par défaut la valeur `Enabled`.  
  
#### Pour activer l'invite d'approbation ClickOnce par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\# dans Visual Studio.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Générez et exécutez l'application.  
  
## Restriction de l'invite d'approbation ClickOnce  
 Restreignez l'invite d'approbation afin que les solutions soient signées avec des certificats Authenticode dont l'identité est connue avant que les utilisateurs ne soient invités à indiquer une décision d'approbation.  
  
#### Pour restreindre l'invite d'approbation ClickOnce à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez `regedit`, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si cette clé n'existe pas, créez\-la.  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées présentées dans le tableau suivant.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### Pour restreindre l'invite d'approbation ClickOnce par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\# dans Visual Studio.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Générez et exécutez l'application.  
  
## Désactivation de l'invite d'approbation ClickOnce  
 Vous pouvez désactiver l'invite d'approbation afin que les utilisateurs finaux ne puissent pas installer de solutions qui ne sont pas déjà approuvées dans leur stratégie de sécurité.  
  
#### Pour désactiver l'invite d'approbation ClickOnce à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez `regedit`, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si cette clé n'existe pas, créez\-la.  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées présentées dans le tableau suivant.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### Pour désactiver l'invite d'approbation ClickOnce par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\# dans Visual Studio.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Générez et exécutez l'application.  
  
## Voir aussi  
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vue d'ensemble du déploiement d'applications approuvées](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Comment : définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Comment : définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Comment : déboguer une application ClickOnce avec des autorisations restreintes](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Comment : ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
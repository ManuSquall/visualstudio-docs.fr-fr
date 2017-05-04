---
title: "Comment&#160;: configurer la s&#233;curit&#233; de la liste d&#39;inclusion | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "listes d'inclusion (développement Office dans Visual Studio)"
  - "autorisations (développement Office dans Visual Studio)"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: configurer la s&#233;curit&#233; de la liste d&#39;inclusion
  Si vous avez des autorisations d'administrateur, vous pouvez configurer l'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pour déterminer si les utilisateurs finaux peuvent installer les solutions Office en enregistrant une décision d'approbation dans la liste d'inclusion.  Pour plus d'informations sur les listes d'inclusion, consultez [Octroi de niveaux de confiance à des solutions Office à l'aide de listes d'inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Pour les solutions figurant dans chacune des cinq zones, vous pouvez définir les options suivantes :  
  
-   Activez la clé d'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] et la liste d'inclusion.  Vous pouvez permettre aux utilisateurs finaux d'approuver les solutions Office signées à l'aide d'un certificat.  
  
-   Restreignez la clé d'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] et la liste d'inclusion.  Vous pouvez permettre aux utilisateurs finaux d'installer des solutions Office signées à l'aide d'un certificat qui identifie l'éditeur, mais qui n'est pas encore approuvé.  
  
-   Désactivez la clé d'invite d'approbation [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] et la liste d'inclusion.  Vous pouvez empêcher les utilisateurs finaux d'installer des solutions Office qui ne sont pas signées avec un certificat explicitement approuvé.  
  
## Activation de la liste d'inclusion  
 Activez la liste d'inclusion pour une zone si vous souhaitez que les utilisateurs finaux aient la possibilité d'installer et d'exécuter les solutions Office provenant de cette zone.  
  
#### Pour activer la liste d'inclusion à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si cette clé n'existe pas, créez\-la.  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Activé**|  
    |**LocalIntranet**|**Activé**|  
    |**TrustedSites**|**Activé**|  
  
     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **Disabled**.  
  
#### Pour activer la liste d'inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Restriction de la liste d'inclusion  
 Restreignez la liste d'inclusion afin que les solutions doivent être signées avec des certificats Authenticode dont l'identité est connue avant que les utilisateurs soient invités à indiquer une décision d'approbation.  
  
#### Pour restreindre la liste d'inclusion  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Recherchez la clé de Registre suivante :  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Si cette clé n'existe pas, créez\-la.  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **Disabled**.  
  
#### Pour restreindre la liste d'inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Désactivation de la liste d'inclusion  
 Vous pouvez désactiver la liste d'inclusion afin que les utilisateurs finaux ne puissent installer que des solutions signées avec un certificat approuvé et connu.  
  
#### Pour désactiver la liste d'inclusion  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la zone **Ouvrir**, tapez **regedt32.exe**, puis cliquez sur **OK**.  
  
2.  Créez la clé de Registre suivante si elle n'existe pas encore :  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  Ajoutez les sous\-clés suivantes en tant que **Valeur chaîne**, si elles n'existent pas encore, avec les valeurs associées.  
  
    |Sous\-clé Valeur chaîne|Valeur|  
    |-----------------------------|------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**LocalIntranet**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### Pour désactiver la liste d'inclusion par programmation  
  
1.  Créez une application console Visual Basic ou Visual C\#.  
  
2.  Ouvrez le fichier Program.vb ou Program.cs à modifier et ajoutez le code suivant.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
 [Octroi de niveaux de confiance à des solutions Office à l'aide de listes d'inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)  
  
  
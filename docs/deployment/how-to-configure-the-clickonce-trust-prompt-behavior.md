---
title: Configurer le comportement de l’invite d’approbation ClickOnce | Microsoft Docs
description: Découvrez comment configurer l’invite d’approbation ClickOnce pour contrôler si les utilisateurs finaux ont la possibilité d’installer des applications ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8cb23eeee53990113d779e241adb8dcf1ab0cf16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890303"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Guide pratique pour configurer le comportement de l’invite d’approbation ClickOnce
Vous pouvez configurer l’invite d’approbation ClickOnce pour contrôler si les utilisateurs finaux ont la possibilité d’installer des applications ClickOnce, telles que des applications Windows Forms, des applications Windows Presentation Foundation, des applications console, des applications de navigateur WPF et des solutions Office. Vous configurez l’invite d’approbation en définissant les clés de Registre sur l’ordinateur de chaque utilisateur final.

 Le tableau suivant présente les options de configuration qui peuvent être appliquées à chacune des cinq zones (Internet, UntrustedSites, MyComputer, LocalIntranet et TrustedSites).

|Option|Valeur du paramètre du Registre|Description|
|------------|----------------------------|-----------------|
|Activez l’invite d’approbation.|`Enabled`|L’invite d’approbation ClickOnce s’affiche afin que les utilisateurs finaux puissent accorder une confiance aux applications ClickOnce.|
|Limitez l’invite d’approbation.|`AuthenticodeRequired`|L’invite d’approbation ClickOnce s’affiche uniquement si les applications ClickOnce sont signées avec un certificat qui identifie le serveur de publication.|
|Désactivez l’invite d’approbation.|`Disabled`|L’invite d’approbation ClickOnce n’est pas affichée pour les applications ClickOnce qui ne sont pas signées avec un certificat explicitement approuvé.|

 Le tableau suivant indique le comportement par défaut de chaque zone. La colonne applications fait référence aux applications Windows Forms, aux applications de Windows Presentation Foundation, aux applications de navigateur WPF et aux applications console.

|Zone|Applications|solutions Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Vous pouvez remplacer ces paramètres en activant, en restreignant ou en désactivant l’invite d’approbation ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Activer l’invite d’approbation ClickOnce
 Activez l’invite d’approbation pour une zone lorsque vous souhaitez que les utilisateurs finaux puissent installer et exécuter toute application ClickOnce qui provient de cette zone.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Pour activer l’invite d’approbation ClickOnce à l’aide de l’éditeur du Registre

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez `regedit` , puis cliquez sur **OK**.

2. Recherchez la clé de Registre suivante :

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Pour les solutions Office, `Internet` possède la valeur par défaut `AuthenticodeRequired` et `UntrustedSites` possède la valeur `Disabled` . Pour tous les autres, `Internet` a la valeur par défaut `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Pour activer l’invite d’approbation ClickOnce par programmation

1. Créez une application console Visual Basic ou Visual C# dans Visual Studio.

2. Ouvrez le fichier *Program. vb* ou *Program.cs* pour le modifier, puis ajoutez le code suivant.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
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

3. Générez et exécutez l’application.

## <a name="restrict-the-clickonce-trust-prompt"></a>Restreindre l’invite d’approbation ClickOnce
 Limitez l’invite d’approbation afin que les solutions doivent être signées avec des certificats Authenticode ayant une identité connue avant que les utilisateurs ne soient invités à prendre une décision d’approbation.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Pour restreindre l’invite d’approbation ClickOnce à l’aide de l’éditeur du Registre

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez `regedit` , puis cliquez sur **OK**.

2. Recherchez la clé de Registre suivante :

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Pour restreindre l’invite d’approbation ClickOnce par programmation

1. Créez une application console Visual Basic ou Visual C# dans Visual Studio.

2. Ouvrez le fichier *Program. vb* ou *Program.cs* pour le modifier, puis ajoutez le code suivant.

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

3. Générez et exécutez l’application.

## <a name="disable-the-clickonce-trust-prompt"></a>Désactiver l’invite d’approbation ClickOnce
 Vous pouvez désactiver l’invite d’approbation afin que les utilisateurs finaux ne puissent pas installer les solutions qui ne sont pas déjà approuvées dans leur stratégie de sécurité.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Pour désactiver l’invite d’approbation ClickOnce à l’aide de l’éditeur du Registre

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez `regedit` , puis cliquez sur **OK**.

2. Recherchez la clé de Registre suivante :

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Pour désactiver l’invite d’approbation ClickOnce par programmation

1. Créez une application console Visual Basic ou Visual C# dans Visual Studio.

2. Ouvrez le fichier *Program. vb* ou *Program.cs* pour le modifier, puis ajoutez le code suivant.

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

3. Générez et exécutez l’application.

## <a name="see-also"></a>Voir aussi
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Sécurité d’accès du code pour les applications ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)
- [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)
- [Guide pratique pour activer les paramètres de sécurité ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Comment : définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](securing-clickonce-applications.md)
- [Guide pratique pour ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Guide pratique pour resigner des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md)

---
title: Comment configurer le comportement d’invite ClickOnce Trust (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649148"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Guide pratique pour configurer le comportement de l’invite d’approbation ClickOnce
Vous pouvez configurer l’invite ClickOnce trust pour contrôler si les utilisateurs finaux ont la possibilité d’installer des applications ClickOnce, telles que les applications Windows Forms, les applications de la Fondation de présentation Windows, les applications de console, les applications de navigateur WPF et les solutions Office. Vous configurez l’invite de confiance en définissant les clés de registre sur l’ordinateur de chaque utilisateur final.

 Le tableau suivant montre les options de configuration qui peuvent être appliquées à chacune des cinq zones (Internet, UntrustedSites, MyComputer, LocalIntranet et TrustedSites).

|Option|Valeur de réglage du registre|Description|
|------------|----------------------------|-----------------|
|Activez la confiance rapidement.|`Enabled`|L’invite ClickOnce trust est l’affichage afin que les utilisateurs finaux peuvent accorder la confiance aux applications ClickOnce.|
|Limitez la confiance prompte.|`AuthenticodeRequired`|L’invite ClickOnce trust n’est affichée que si les applications ClickOnce sont signées avec un certificat qui identifie l’éditeur.|
|Désactiver l’invite de confiance.|`Disabled`|L’invite ClickOnce trust n’est pas affichée pour les applications ClickOnce qui ne sont pas signées avec un certificat explicitement fiable.|

 Le tableau suivant montre le comportement par défaut pour chaque zone. La colonne Applications se réfère aux applications Windows Forms, aux applications de la Fondation de présentation Windows, aux applications du navigateur WPF et aux applications consoles.

|Zone|Applications|solutions Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Vous pouvez remplacer ces paramètres en activant, en limitant ou en désactivant l’invite ClickOnce trust.

## <a name="enable-the-clickonce-trust-prompt"></a>Activez l’invite ClickOnce trust
 Activez l’invite de confiance pour une zone lorsque vous souhaitez que les utilisateurs finaux soient présentés avec la possibilité d’installer et d’exécuter n’importe quelle application ClickOnce qui vient de cette zone.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Pour activer l’invite ClickOnce trust en utilisant l’éditeur du registre

1. Ouvrez l’éditeur du registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la boîte `regedit` **ouverte,** tapez, puis cliquez **sur OK**.

2. Trouvez la clé de registre suivante :

     **HKEY_LOCAL_MACHINE-SOFTWARE.MICROSOFT\\. NETFramework-Security-TrustManager-PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes sous forme **de valeur de chaîne,** si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de la chaîne|Valeur|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Pour les `Internet` solutions Office, `AuthenticodeRequired` `UntrustedSites` a la `Disabled`valeur par défaut et a la valeur . Pour tous `Internet` les autres, `Enabled`a la valeur par défaut .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Pour activer la fiducie ClickOnce, invitez programmatiquement

1. Créez une application de console Visual Basic ou Visual CMD dans Visual Studio.

2. Ouvrez le *fichier Program.vb* ou *Program.cs* pour l’édition et ajoutez le code suivant.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Limiter l’invite ClickOnce trust
 Limitez l’invite de confiance afin que des solutions doivent être signées avec des certificats Authenticode qui ont connu l’identité avant que les utilisateurs soient invités à une décision de fiducie.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Restreindre l’invite clickOnce trust en utilisant l’éditeur du registre

1. Ouvrez l’éditeur du registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la boîte `regedit` **ouverte,** tapez, puis cliquez **sur OK**.

2. Trouvez la clé de registre suivante :

     **HKEY_LOCAL_MACHINE-SOFTWARE.MICROSOFT\\. NETFramework-Security-TrustManager-PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes sous forme **de valeur de chaîne,** si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de la chaîne|Valeur|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Limiter la fiducie ClickOnce invite programmatiquement

1. Créez une application de console Visual Basic ou Visual CMD dans Visual Studio.

2. Ouvrez le *fichier Program.vb* ou *Program.cs* pour l’édition et ajoutez le code suivant.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Désactiver l’invite clickOnce trust
 Vous pouvez désactiver l’invite de confiance de sorte que les utilisateurs finaux ne sont pas donnés la possibilité d’installer des solutions qui ne sont pas déjà confiance dans leur politique de sécurité.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Pour désactiver l’invite ClickOnce trust en utilisant l’éditeur du registre

1. Ouvrez l’éditeur du registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la boîte `regedit` **ouverte,** tapez, puis cliquez **sur OK**.

2. Trouvez la clé de registre suivante :

     **HKEY_LOCAL_MACHINE-SOFTWARE.MICROSOFT\\. NETFramework-Security-TrustManager-PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes sous forme **de valeur de chaîne,** si elles n’existent pas déjà, avec les valeurs associées indiquées dans le tableau suivant.

    |Sous-clé de valeur de la chaîne|Valeur|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Pour désactiver la fiducie ClickOnce invite programmatiquement

1. Créez une application de console Visual Basic ou Visual CMD dans Visual Studio.

2. Ouvrez le *fichier Program.vb* ou *Program.cs* pour l’édition et ajoutez le code suivant.

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
- [Comment : Définir une zone de sécurité pour une application ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Guide pratique pour définir des autorisations personnalisées pour une application ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](securing-clickonce-applications.md)
- [Guide pratique pour ajouter un éditeur approuvé à un ordinateur client pour les applications ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Guide pratique pour resigner des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md)

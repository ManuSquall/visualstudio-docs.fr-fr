---
title: 'Comment : configurer la sécurité de la liste d’inclusion'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541633"
---
# <a name="how-to-configure-inclusion-list-security"></a>Comment : configurer la sécurité de la liste d’inclusion
  Si vous disposez d’autorisations d’administrateur, vous pouvez configurer l' [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation pour contrôler si les utilisateurs finaux ont la possibilité d’installer des solutions Office en enregistrant une décision d’approbation dans la liste d’inclusion. Pour plus d’informations sur les listes d’inclusion, consultez [approuver des solutions Office à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pour les solutions qui se trouvent dans chacune des cinq zones, vous pouvez définir les options suivantes :

- Activez la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et la liste d’inclusion. Vous pouvez autoriser les utilisateurs finaux à accorder un niveau de confiance à des solutions Office signées avec n’importe quel certificat.

- Limitez la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et la liste d’inclusion. Vous pouvez autoriser les utilisateurs finaux à installer des solutions Office signées avec un certificat qui identifie le serveur de publication, mais qui n’est pas déjà approuvé.

- Désactivez la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et la liste d’inclusion. Vous pouvez empêcher les utilisateurs finaux d’installer une solution Office qui n’est pas signée avec un certificat explicitement approuvé.

## <a name="enable-the-inclusion-list"></a>Activer la liste d’inclusion
 Activez la liste d’inclusion pour une zone lorsque vous souhaitez que les utilisateurs finaux aient la possibilité d’installer et d’exécuter une solution Office provenant de cette zone.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Pour activer la liste d’inclusion à l’aide de l’éditeur du Registre

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2. Recherchez la clé de Registre suivante :

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Désactivé**|
    |**MyComputer**|**Activé**|
    |**LocalIntranet**|**Activé**|
    |**TrustedSites**|**Activé**|

     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **Disabled**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Pour activer la liste d’inclusion par programmation

1. Créez une application console Visual Basic ou Visual C#.

2. Ouvrez le fichier *Program. vb* ou *Program.cs* pour le modifier, puis ajoutez le code suivant.

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

3. Générez et exécutez l’application.

## <a name="restrict-the-inclusion-list"></a>Restreindre la liste d’inclusion
 Limitez la liste d’inclusion afin que les solutions doivent être signées avec des certificats Authenticode dont l’identité est connue avant que les utilisateurs ne soient invités à prendre une décision d’approbation.

### <a name="to-restrict-the-inclusion-list"></a>Pour limiter la liste d’inclusion

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2. Recherchez la clé de Registre suivante :

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-la.

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |**UntrustedSites**|**Désactivé**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **Disabled**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Pour limiter la liste d’inclusion par programmation

1. Créez une application console Visual Basic ou Visual C#.

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

## <a name="disable-the-inclusion-list"></a>Désactiver la liste d’inclusion
 Vous pouvez désactiver la liste d’inclusion afin que les utilisateurs finaux puissent uniquement installer les solutions signées avec un certificat approuvé et connu.

### <a name="to-disable-the-inclusion-list"></a>Pour désactiver la liste d’inclusion

1. Ouvrez l’éditeur du Registre :

    1. Cliquez sur **Démarrer**, puis sur **Exécuter**.

    2. Dans la zone **ouvrir** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2. Créez la clé de Registre suivante si elle n’existe pas déjà :

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

3. Ajoutez les sous-clés suivantes comme **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Valeur|
    |-------------------------|-----------|
    |**UntrustedSites**|**Désactivé**|
    |**Internet**|**Désactivé**|
    |**MyComputer**|**Désactivé**|
    |**LocalIntranet**|**Désactivé**|
    |**TrustedSites**|**Désactivé**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Pour désactiver la liste d’inclusion par programmation

1. Créez une application console Visual Basic ou Visual C#.

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
- [Approuver des solutions Office à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)

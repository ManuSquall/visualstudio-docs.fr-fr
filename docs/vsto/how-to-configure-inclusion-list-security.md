---
title: 'Procédure : Configurer la sécurité de liste d’inclusion'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 1277499fd0af52a4e7138637ef8be332b56a4926
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596475"
---
# <a name="how-to-configure-inclusion-list-security"></a>Procédure : Configurer la sécurité de liste d’inclusion
  Si vous disposez des autorisations d’administrateur, vous pouvez configurer le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation pour contrôler si les utilisateurs finaux reçoivent la possibilité d’installer les solutions Office en enregistrant une décision d’approbation dans la liste d’inclusion. Pour plus d’informations sur les listes d’inclusion, consultez [solutions Office faire confiance à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pour les solutions qui se trouvent dans chacune des cinq zones, vous pouvez définir les options suivantes :

-   Activer la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez autoriser les utilisateurs finaux d’approuver des solutions Office qui sont signés avec n’importe quel certificat.

-   Restreindre la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez autoriser les utilisateurs finaux installer les solutions Office signées avec un certificat qui identifie le serveur de publication, mais qui n’est pas approuvé.

-   Désactiver la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation et de la liste d’inclusion. Vous pouvez empêcher les utilisateurs finaux à partir de l’installation de toute solution Office qui n’est pas signée avec un certificat explicitement approuvé.

## <a name="enable-the-inclusion-list"></a>Activer la liste d’inclusion
 Activer la liste d’inclusion d’une zone lorsque vous souhaitez que les utilisateurs finaux aient la possibilité d’installer et exécuter les solutions Office provenant de cette zone.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Pour activer la liste d’inclusion à l’aide de l’Éditeur du Registre

1.  Ouvrez l’Éditeur du Registre :

    1.  Cliquez sur **Démarrer** puis sur **Exécuter**.

    2.  Dans le **Open** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2.  Recherchez la clé de Registre suivante :

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-le.

3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Value|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Désactivé**|
    |**MyComputer**|**Activé**|
    |**LocalIntranet**|**Activé**|
    |**TrustedSites**|**Activé**|

     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **désactivé**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Pour activer la liste d’inclusion par programmation

1.  Créer une application console Visual Basic ou Visual c#.

2.  Ouvrez le *Program.vb* ou *Program.cs* fichier pour le modifier, puis ajoutez le code suivant.

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

3.  Générez et exécutez l’application.

## <a name="restrict-the-inclusion-list"></a>Restreindre la liste d’inclusion
 Limiter la liste d’inclusion de sorte que les solutions doivent être signées avec des certificats Authenticode dont l’identité est connue avant que les utilisateurs soient invités à une décision d’approbation.

### <a name="to-restrict-the-inclusion-list"></a>Pour restreindre la liste d’inclusion

1.  Ouvrez l’Éditeur du Registre :

    1.  Cliquez sur **Démarrer** puis sur **Exécuter**.

    2.  Dans le **Open** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2.  Recherchez la clé de Registre suivante :

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Si la clé n’existe pas, créez-le.

3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Value|
    |-------------------------|-----------|
    |**UntrustedSites**|**Désactivé**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Par défaut, **Internet** a la valeur **AuthenticodeRequired** et **UntrustedSites** a la valeur **désactivé**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Pour restreindre la liste d’inclusion par programmation

1.  Créer une application console Visual Basic ou Visual c#.

2.  Ouvrez le *Program.vb* ou *Program.cs* fichier pour le modifier, puis ajoutez le code suivant.

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

3.  Générez et exécutez l’application.

## <a name="disable-the-inclusion-list"></a>Désactiver la liste d’inclusion
 Vous pouvez désactiver la liste d’inclusion afin que les utilisateurs finaux peuvent installer uniquement les solutions qui sont signées avec un certificat approuvé et connu.

### <a name="to-disable-the-inclusion-list"></a>Pour désactiver la liste d’inclusion

1.  Ouvrez l’Éditeur du Registre :

    1.  Cliquez sur **Démarrer** puis sur **Exécuter**.

    2.  Dans le **Open** , tapez **regedt32.exe**, puis cliquez sur **OK**.

2.  Créez la clé de Registre suivante si cela n’existe pas déjà :

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

3.  Ajoutez les sous-clés suivantes en tant que **valeur de chaîne**, si elles n’existent pas déjà, avec les valeurs associées.

    |Sous-clé de valeur de chaîne|Value|
    |-------------------------|-----------|
    |**UntrustedSites**|**Désactivé**|
    |**Internet**|**Désactivé**|
    |**MyComputer**|**Désactivé**|
    |**LocalIntranet**|**Désactivé**|
    |**TrustedSites**|**Désactivé**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Pour désactiver la liste d’inclusion par programmation

1.  Créer une application console Visual Basic ou Visual c#.

2.  Ouvrez le *Program.vb* ou *Program.cs* fichier pour le modifier, puis ajoutez le code suivant.

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

3.  Générez et exécutez l’application.

## <a name="see-also"></a>Voir aussi
- [Approuver des solutions Office à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)

---
title: '&lt;&gt;élément trustInfo (application ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5873eb18b2f803acfd5aba9444657884b1a24581
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184430"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt;, élément (application ClickOnce)
Décrit les autorisations de sécurité minimales dont doit disposer l’application pour qu’elle s’exécute sur l’ordinateur client.

## <a name="syntax"></a>Syntaxe

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `trustInfo` est obligatoire et se trouve dans l’espace de noms `asm.v2` . Il n’a aucun attribut et contient les éléments suivants.

## <a name="security"></a>security
 Obligatoire. Cet élément est un enfant de l’élément `trustInfo` . Il contient l’élément `applicationRequestMinimum` et n’a pas d’attributs.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Obligatoire. Cet élément est un enfant de l’élément `security` et contient les éléments `PermissionSet`, `assemblyRequest`et `defaultAssemblyRequest`. Cet élément n’a pas d’attributs.

## <a name="permissionset"></a>PermissionSet
 Obligatoire. Cet élément est un enfant de l’élément `applicationRequestMinimum` et contient l’élément `IPermission` . Cet élément comprend les attributs suivants.

- `ID`

     Obligatoire. Identifie le jeu d’autorisations. Cet attribut peut avoir n’importe quelle valeur. L’ID est référencé dans les attributs `defaultAssemblyRequest` et `assemblyRequest` .

- `version`

     Obligatoire. Identifie la version de l’autorisation. En général, cette valeur est égale à `1`.

## <a name="ipermission"></a>IPermission
 facultatif. Cet élément est un enfant de l’élément `PermissionSet` . L' `IPermission` élément identifie entièrement une classe d’autorisation dans le .NET Framework. L’élément `IPermission` comprend les attributs suivants, mais il peut en avoir d’autres qui correspondent aux propriétés de la classe d’autorisation. Pour trouver la syntaxe d’une autorisation spécifique, consultez les exemples figurant dans le fichier Security.config.

- `class`

     Obligatoire. Identifie la classe d’autorisation par son nom fort. Par exemple, le code suivant identifie le type `FileDialogPermission` .

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Obligatoire. Identifie la version de l’autorisation. En général, cette valeur est égale à `1`.

- `Unrestricted`

     Obligatoire. Indique si l’application doit se voir accorder cette autorisation sans aucune limite. Si cet attribut a la valeur `true`, l’autorisation est accordée à l’application de manière inconditionnelle. Si cet attribut a la valeur `false`, ou s’il n’est pas défini, des restrictions sont imposées à l’application en fonction d’attributs spécifiques à l’autorisation définis dans la balise `IPermission` . Prenez les autorisations suivantes :

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     Dans cet exemple, la déclaration d’ <xref:System.Security.Permissions.EnvironmentPermission> indique que l’application peut uniquement lire la variable d’environnement USERNAME, tandis que la déclaration de <xref:System.Security.Permissions.FileDialogPermission> permet à l’application d’utiliser toutes les classes <xref:System.Windows.Forms.FileDialog> sans aucune restriction.

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 facultatif. Identifie le jeu d’autorisations accordé à tous les assemblys. Cet élément est un enfant de l’élément `applicationRequestMinimum` et contient l’attribut suivant.

- `permissionSetReference`

     Obligatoire. Identifie l’ID du jeu d’autorisations qui est l’autorisation par défaut. Le jeu d’autorisations est déclaré dans l’élément `PermissionSet` .

## <a name="assemblyrequest"></a>assemblyRequest
 facultatif. Identifie les autorisations d’un assembly spécifique. Cet élément est un enfant de l’élément `applicationRequestMinimum` et comprend les attributs suivants.

- `Name`

     Obligatoire. Identifie le nom de l’assembly.

- `permissionSetReference`

     Obligatoire. Identifie l’ID du jeu d’autorisations dont a besoin cet assembly. Le jeu d’autorisations est déclaré dans l’élément `PermissionSet` .

## <a name="requestedprivileges"></a>requestedPrivileges
 facultatif. Cet élément est un enfant de l’élément `security` et contient l’élément `requestedExecutionLevel` . Cet élément n’a pas d’attributs.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 facultatif. Identifie le niveau de sécurité auquel les demandes d’application doivent être exécutées. Cet élément n’a pas d’enfants et comprend les attributs suivants.

- `Level`

   Obligatoire. Indique le niveau de sécurité demandé par l’application. Les valeurs possibles sont les suivantes :

   `asInvoker`: ne demande aucune autorisation supplémentaire. Ce niveau ne nécessite aucune invite d’approbation supplémentaire.

   `highestAvailable`: demande les autorisations les plus élevées pouvant être octroyées au processus parent.

   `requireAdministrator`: demande d’autorisations d’administrateur complètes.

   Les applications[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont uniquement installées avec la valeur `asInvoker`. Toute installation effectuée avec une autre valeur se soldera par un échec.

- `uiAccess`

   facultatif. Indique si l’application nécessite l’accès aux éléments protégés de l’interface utilisateur. La valeur peut être `true` ou `false`(false étant la valeur par défaut). Seules les applications signées doivent avoir la valeur true.

## <a name="remarks"></a>Remarques
 Si une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] demande davantage d’autorisations que celles accordées par défaut par l’ordinateur client, le Gestionnaire de confiance du common language runtime demande à l’utilisateur s’il souhaite accorder à l’application ce niveau de privilège élevé. S’il refuse, l’application ne fonctionne pas ; s’il accepte, elle s’exécute avec les autorisations demandées.

 Toutes les autorisations demandées à l’aide de `defaultAssemblyRequest` et d’ `assemblyRequest` sont accordées sans demander confirmation à l’utilisateur si le manifeste de déploiement dispose d’une licence de confiance valide.

 Pour plus d’informations sur l’élévation d’autorisations, consultez [sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md). Pour plus d’informations sur le déploiement de stratégies, consultez [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Exemples
 Les trois exemples de code suivants illustrent les éléments `trustInfo` pour les zones de sécurité nommées par défaut (Internet, LocalIntranet et FullTrust). Vous utilisez ces éléments dans le manifeste d’application d’un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Le premier exemple illustre l’élément `trustInfo` pour les autorisations par défaut disponibles dans la zone de sécurité Internet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Le deuxième exemple illustre l’élément `trustInfo` pour les autorisations par défaut disponibles dans la zone de sécurité LocalIntranet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 Le troisième exemple illustre l’élément `trustInfo` pour les autorisations par défaut disponibles dans la zone de sécurité FullTrust.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du déploiement d’applications approuvées](../deployment/trusted-application-deployment-overview.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
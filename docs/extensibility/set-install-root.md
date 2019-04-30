---
title: L’installation en dehors du dossier d’extensions avec VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09b3b23a89450bb1abac4f8ebb10d00396a251b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433146"
---
# <a name="installing-outside-the-extensions-folder"></a>L’installation en dehors du dossier d’extensions

En commençant par Visual Studio 2017 et VSIX v3 (version 3), il est prennent désormais en charge pour l’installation des composants d’extension en dehors du dossier extensions. Actuellement, les emplacements suivants sont activés en tant qu’emplacements d’installation valide (où [INSTALLDIR] est mappé au répertoire d’installation de l’instance de Visual Studio) :

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**Remarque :** Le format VSIX ne vous permet pas d’installer en dehors de la structure de dossiers d’installation Visual Studio.

Pour prendre en charge l’installation de ces répertoires, l’extension VSIX doit être installé « par instance par ordinateur ». Cette option peut être activée en cochant la case « tous les utilisateurs » dans le concepteur extension.vsixmanifest :

![Vérifiez tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Comment définir le InstallRoot

Pour définir les répertoires d’installation, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio. Par exemple, vous pouvez définir le `InstallRoot` propriété d’une référence de projet à un des emplacements ci-dessus :

![propriétés de la racine d’installation](media/install-root-properties.png)

Cette opération ajoute des métadonnées correspondant `ProjectReference` propriété à l’intérieur du fichier de .csproj du projet VSIX :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Remarque :** Vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Comment définir un sous-chemin sous le InstallRoot

Si vous souhaitez installer sur un sous-chemin sous la `InstallRoot`, vous pouvez le faire en définissant le `VsixSubPath` propriété tout comme le `InstallRoot` propriété. Par exemple, si nous voulons la sortie de la référence de notre projet à installer pour ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0 ». Nous pouvons le faire facilement avec le Concepteur de la propriété :

![sous-chemin de jeu](media/set-subpath.png)

Les modifications correspondantes de .csproj ressemblera à ceci :

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informations supplémentaires

Les modifications de Concepteur de propriété s’appliquent aux plus que les références de projet ; Vous pouvez définir le `InstallRoot` métadonnées des éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus).

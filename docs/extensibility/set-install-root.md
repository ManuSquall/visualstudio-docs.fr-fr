---
title: "L’installation en dehors du dossier extensions avec VSIX v3 | Documents Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b604a70c44b6fd25888ee5419efbb95f95a0a4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="installing-outside-the-extensions-folder"></a>L’installation en dehors du dossier d’extensions

En commençant par Visual Studio 2017 et VSIX v3 (version 3), désormais une prise en charge pour l’installation des composants d’extension en dehors du dossier extensions. Actuellement, les emplacements suivants sont activés en tant qu’emplacements d’installation valide (où [INSTALLDIR] est mappé au répertoire d’installation de l’instance de Visual Studio) :

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**Remarque :** le format VSIX ne vous permet pas d’installer à l’extérieur de la structure de dossiers d’installation Visual Studio.

Pour prendre en charge l’installation de ces répertoires, l’extension VSIX doit être installé « par instance par ordinateur ». Cela peut être activé en activant la case à cocher « tous les utilisateurs » dans le concepteur extension.vsixmanifest :

![Vérifiez tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Comment définir le InstallRoot

Pour définir les répertoires d’installation, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio. Par exemple, vous pouvez définir le `InstallRoot` propriété d’une référence de projet à un des emplacements ci-dessus :

![installer les propriétés racine](media/install-root-properties.png)

Cela ajoutera des métadonnées correspondant `ProjectReference` propriété à l’intérieur du fichier .csproj du projet VSIX :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Remarque :** vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Comment définir un sous-chemin sous le InstallRoot

Si vous souhaitez installer un sous-chemin sous le `InstallRoot`, vous pouvez le faire en définissant le `VsixSubPath` propriété tout comme le `InstallRoot` propriété. Par exemple, nous souhaitons sortie de notre référence projet à installer pour ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. Nous pouvons faire cela facilement avec le Concepteur de la propriété :

![sous-chemin de jeu](media/set-subpath.png)

Les modifications correspondantes de .csproj doit ressembler à ceci :

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informations supplémentaires

Les modifications concepteur des propriétés s’appliquent aux plus que les références de projet ; Vous pouvez définir le `InstallRoot` métadonnées des éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus).

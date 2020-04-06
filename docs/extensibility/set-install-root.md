---
title: Installation à l’extérieur du dossier d’extensions avec VSIX v3 Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700182"
---
# <a name="install-outside-the-extensions-folder"></a>Installer en dehors du dossier d’extensions

En commençant par Visual Studio 2017 et VSIX v3 (version 3), les actifs d’extension peuvent être installés en dehors du dossier d’extensions. Actuellement, les emplacements suivants sont activés en tant qu’emplacements d’installation valides (où [INSTALLDIR] est cartographié au répertoire d’installation de l’instance Visual Studio) :

* [INSTALLDIR]
* [INSTALLDIR]
* [INSTALLDIR]
* [INSTALLDIR]-Licences
* [INSTALLDIR]
* [INSTALLDIR]
* [INSTALLDIR] -Common7-IDE-VC-VC-VCTargets (seulement pris en charge pour Visual Studio 2017; déprécié pour Visual Studio 2019 et plus tard)

> [!NOTE]
> Le format VSIX ne vous permet pas d’installer en dehors de la structure de dossier d’installation Visual Studio. 

Afin de soutenir l’installation de ces répertoires, le VSIX doit être installé "par exemple par machine". Cela peut être activé en vérifiant la case à cocher "tous les utilisateurs" dans le concepteur extension.vsixmanifest:

![vérifier tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Comment définir l’InstallRoot

Pour définir les répertoires d’installation, vous pouvez utiliser la fenêtre **Properties** dans Visual Studio. Par exemple, vous `InstallRoot` pouvez définir la propriété d’une référence de projet à l’un des endroits ci-dessus :

![installer des propriétés racinaires](media/install-root-properties.png)

Ceci ajoutera quelques métadonnées à la propriété correspondante `ProjectReference` à l’intérieur du fichier .csproj du projet VSIX :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Comment définir un sous-chemin sous le InstallRoot

Si vous souhaitez installer à un sous-chemin sous le , vous pouvez le `InstallRoot`faire en fixant la `VsixSubPath` propriété tout comme la `InstallRoot` propriété. Par exemple, disons que nous voulons que la sortie de notre référence de projet soit installée à '[INSTALLDIR]'MSBuild’MyCompany-MySDK'1.0'. Nous pouvons le faire facilement avec le concepteur de propriété:

![ensemble sous-chemin](media/set-subpath.png)

Les modifications correspondantes .csproj ressemblera à ceci:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informations supplémentaires

Les modifications apportées au concepteur de propriétés s’appliquent à plus que de simples références de projet; vous pouvez `InstallRoot` également définir les métadonnées pour les éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus).

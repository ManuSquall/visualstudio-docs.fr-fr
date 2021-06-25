---
title: Installation en dehors du dossier Extensions avec VSIX v3 | Microsoft Docs
description: En savoir plus sur l’installation des ressources d’extension du kit de développement logiciel Visual Studio en dehors du dossier Extensions et des emplacements valides.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898446"
---
# <a name="install-outside-the-extensions-folder"></a>Installer en dehors du dossier d’extensions

À compter de Visual Studio 2017 et de VSIX v3 (version 3), les ressources d’extension peuvent être installées en dehors du dossier Extensions. Actuellement, les emplacements suivants sont activés en tant qu’emplacements d’installation valides (où [INSTALLDIR] est mappé au répertoire d’installation de l’instance de Visual Studio) :

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (uniquement pris en charge pour Visual Studio 2017 ; déconseillé pour Visual Studio 2019 et versions ultérieures)

> [!NOTE]
> Le format VSIX ne vous permet pas d’installer en dehors de la structure du dossier d’installation de Visual Studio. 

Pour prendre en charge l’installation de sur ces répertoires, le VSIX doit être installé « par ordinateur ». Vous pouvez activer cette option en cochant la case « All-Users » dans le concepteur extension. vsixmanifest :

![vérifier tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Comment définir le InstallRoot

Pour définir les répertoires d’installation, vous pouvez utiliser la fenêtre **Propriétés** dans Visual Studio. Par exemple, vous pouvez définir la `InstallRoot` propriété d’une référence de projet à l’un des emplacements ci-dessus :

![installer les propriétés racine](media/install-root-properties.png)

Cela permet d’ajouter des métadonnées à la `ProjectReference` propriété correspondante dans le fichier. csproj du projet VSIX :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Vous pouvez modifier le fichier. csproj directement, si vous préférez.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Comment définir un sous-tracé sous le InstallRoot

Si vous souhaitez installer un sous-chemin d’accès sous le `InstallRoot` , vous pouvez le faire en définissant la propriété de la `VsixSubPath` même manière que la `InstallRoot` propriété. Par exemple, supposons que la sortie de la référence de projet s’installe sur « [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0 ». Nous pouvons le faire facilement avec le concepteur de propriétés :

![définir le sous-chemin](media/set-subpath.png)

Les modifications. csproj correspondantes se présentent comme suit :

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informations supplémentaires

Les modifications du concepteur de propriétés s’appliquent à plus que simplement des références de projet. vous pouvez également définir les `InstallRoot` métadonnées des éléments à l’intérieur de votre projet (à l’aide des mêmes méthodes que celles décrites ci-dessus).

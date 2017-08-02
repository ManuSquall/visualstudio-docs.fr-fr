---
title: "L’installation en dehors du dossier extensions avec VSIX v3 | Documents Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>L’installation en dehors du dossier extensions

Depuis Visual Studio 2017 et VSIX v3 (version 3), il est prennent désormais en charge pour l’installation des composants d’extension en dehors du dossier extensions. Actuellement, les emplacements suivants sont activés en tant qu’emplacements d’installation valide (où [installdir] est mappé au répertoire d’installation de l’instance de Visual Studio) :

* [installdir] \Common7\IDE\PublicAssemblies
* [installdir] \Common7\IDE\ReferenceAssemblies
* [installdir] \MSBuild
* [installdir] \Schemas
* [installdir] \Licenses
* [installdir] \RemoteDebugger
* [installdir] \VSTargets

>**Remarque :** le format VSIX ne vous permet pas d’installer en dehors de la structure de dossiers d’installation Visual Studio.

Pour prendre en charge l’installation de ces répertoires, cette dernière doit être installée « par instance par ordinateur ». Cela peut être activée en cochant la case « tous les utilisateurs » dans le concepteur extension.vsixmanifest :

![Vérifiez tous les utilisateurs](~/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Comment définir le %InstallRoot%

Pour définir les répertoires d’installation, vous pouvez utiliser la **propriétés** fenêtre dans Visual Studio. Par exemple, vous pouvez définir le `InstallRoot` propriété d’une référence de projet à un des emplacements ci-dessus :

![installer des propriétés de la racine](~/extensibility/media/install-root-properties.png)

Cela ajoutera des métadonnées correspondantes `ProjectReference` propriété à l’intérieur de l’extension VSIX fichier .csproj :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Remarque :** vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Comment définir un sous-chemin sous le %InstallRoot%

Si vous souhaitez installer sur un sous-chemin sous la `InstallRoot`, vous pouvez le faire en définissant le `VsixSubPath` propriété tout comme le `InstallRoot` propriété. Par exemple, nous voulons la sortie de la référence de notre projet à installer sur ' [installdir]\MSBuild\MyCompany\MySDK\1.0'. Nous pouvons le faire facilement avec le Concepteur de la propriété :

![sous-chemin d’ensemble](~/extensibility/media/set-subpath.png)

Les modifications .csproj correspondant doit ressembler à ceci :

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Informations supplémentaires

Les modifications apportées aux propriétés concepteur s’appliquent aux plus que les références de projet ; Vous pouvez définir le `InstallRoot` métadonnées des éléments à l’intérieur de votre projet (en utilisant les mêmes méthodes décrites ci-dessus).


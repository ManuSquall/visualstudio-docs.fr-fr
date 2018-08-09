---
title: Inscription des verbes pour les Extensions de nom de fichier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a47f45889744db51d68c0f8aeb51b11863823965
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639726"
---
# <a name="register-verbs-for-file-name-extensions"></a>Inscrire des verbes pour les extensions de nom de fichier
L’association d’une extension de nom de fichier avec une application a généralement une action par défaut qui se produit lorsqu’un utilisateur double-clique sur un fichier. Cette action est liée à un verbe, par exemple ouvrir, qui correspond à l’action de préférence.  
  
 Vous pouvez inscrire les verbes qui sont associés à un identificateur programmatique (ProgID) pour une extension à l’aide de la clé de Shell situé dans **HKEY_CLASSES_ROOT\{progid} \shell**. Pour plus d’informations, consultez [types de fichiers](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="register-standard-verbs"></a>Inscrire des verbes standard  
 Le système d’exploitation reconnaît les verbes standards suivants :  
  
-   Ouvrir  
  
-   Modifier  
  
-   Lecture  
  
-   Imprimer  
  
-   Preview  
  
 Si possible, inscrivez un verbe standard. Le choix le plus courant est le verbe Open. Utilisez le verbe de modification uniquement s’il existe une différence entre l’ouverture du fichier et en modifiant le fichier. Par exemple, l’ouverture d’un *.htm* fichier l’affiche dans le navigateur, tandis que la modification une *.htm* fichier démarre un éditeur HTML. Les verbes standards sont localisés avec les paramètres régionaux de système d’exploitation.  
  
> [!NOTE]
>  Lors de l’inscription des verbes standard, ne définissez pas la valeur par défaut pour ouvrir la clé. La valeur par défaut contient la chaîne d’affichage dans le menu. Le système d’exploitation fournit cette chaîne des verbes standard.  
  
 Fichiers de projet doivent être inscrits pour démarrer une nouvelle instance de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lorsqu’un utilisateur ouvre le fichier. L’exemple suivant illustre une inscription de verbe standard pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projet.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Pour ouvrir un fichier dans une instance existante de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], enregistrer une clé de DDEEXEC. L’exemple suivant illustre une inscription de verbe standard pour un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs* fichier.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="set-the-default-verb"></a>Définir le verbe par défaut  
 Le verbe par défaut est l’action qui est exécutée quand un utilisateur double-clique sur un fichier dans l’Explorateur Windows. Le verbe par défaut est le verbe spécifié comme valeur par défaut pour le **HKEY_CLASSES_ROOT\\*progid*\Shell** clé. Si aucune valeur n’est spécifiée, le verbe par défaut est le premier verbe spécifié dans le **HKEY_CLASSES_ROOT\\*progid*\Shell** liste de clés.  
  
> [!NOTE]
>  Si vous envisagez de modifier le verbe par défaut pour une extension dans un déploiement côte à côte, envisagez l’impact sur l’installation et la suppression. Lors de l’installation, la valeur par défaut d’origine est remplacée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les associations de fichiers de côte à côte](../extensibility/managing-side-by-side-file-associations.md)

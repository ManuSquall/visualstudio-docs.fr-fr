---
title: Inscription de verbes pour les extensions de nom de fichier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685266"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Inscription des verbes pour les extensions de nom de fichier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’Association d’une extension de nom de fichier à une application a généralement une action préférée qui se produit lorsqu’un utilisateur double-clique sur un fichier. Cette action par défaut est liée à un verbe, par exemple Open, qui correspond à l’action.  
  
 Vous pouvez inscrire des verbes associés à un identificateur programmatique (ProgID) pour une extension à l’aide de la clé de Shell située dans HKEY_CLASSES_ROOT \\ *ProgID*\shell. Pour plus d’informations, consultez [types de fichiers](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Inscription des verbes standard  
 Le système d’exploitation reconnaît les verbes standard suivants :  
  
- Ouvrir  
  
- Modifier  
  
- Lire  
  
- Impression  
  
- Préversion  
  
  Dans la mesure du possible, inscrivez un verbe standard. Le choix le plus courant est le verbe Open. Utilisez le verbe Edit uniquement s’il existe une différence nette entre l’ouverture du fichier et la modification du fichier. Par exemple, l’ouverture d’un fichier. htm l’affiche dans le navigateur, tandis que la modification d’un fichier. htm démarre un éditeur HTML. Les verbes standard sont localisés avec les paramètres régionaux du système d’exploitation.  
  
> [!NOTE]
> Lors de l’inscription des verbes standard, ne définissez pas la valeur par défaut de la clé ouverte. La valeur par défaut contient la chaîne d’affichage dans le menu. Le système d’exploitation fournit cette chaîne pour les verbes standard.  
  
 Les fichiers projet doivent être inscrits pour démarrer une nouvelle instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lorsqu’un utilisateur ouvre le fichier. L’exemple suivant illustre une inscription de verbe standard pour un [!INCLUDE[csprcs](../includes/csprcs-md.md)] projet.  
  
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
  
 Pour ouvrir un fichier dans une instance existante de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , inscrivez une clé DDEEXEC. L’exemple suivant illustre une inscription de verbe standard pour un [!INCLUDE[csprcs](../includes/csprcs-md.md)] fichier. cs.  
  
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
  
## <a name="setting-the-default-verb"></a>Définition du verbe par défaut  
 Le verbe par défaut est l’action qui est exécutée lorsqu’un utilisateur double-clique sur un fichier dans l’Explorateur Windows. Le verbe par défaut est le verbe spécifié comme valeur par défaut pour l’HKEY_CLASSES_ROOT \\ clé de \Shell*ProgID*. Si aucune valeur n’est spécifiée, le verbe par défaut est le premier verbe spécifié dans la liste de clés de HKEY_CLASSES_ROOT \\ *ProgID*\Shell.  
  
> [!NOTE]
> Si vous envisagez de modifier le verbe par défaut pour une extension dans un déploiement côte à côte, prenez en compte l’impact sur l’installation et la suppression. Pendant l’installation, la valeur par défaut d’origine est remplacée.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)

---
title: -Edit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c4dabbb0c21fd6b4cabb01655485c8158662adb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422329"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ouvre le fichier spécifié dans une instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Arguments  
 `file1`  
 Optionnel. Fichier à ouvrir dans une instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Si aucune instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] n’existe, une instance est créée avec une disposition de fenêtre simplifiée et `file1` est ouvert dans la nouvelle instance.  
  
 `file2`  
 Optionnel. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="remarks"></a>Remarques  
 Si aucun fichier n’est spécifié et qu’il existe une instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] reçoit le focus. Si aucun fichier n’est spécifié et qu’il n’y a aucune instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], une instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est créée avec une disposition de fenêtre simplifiée.  
  
 Si l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est dans un état modal, par exemple si la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte, le fichier s’ouvre dans l’instance existante quand [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] quitte l’état modal.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre le fichier `MyFile.cs` dans une instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou dans une nouvelle instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s’il n’en existe pas déjà une.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)

---
title: -Edit (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe3adb8967c7571a320bcdf840df6f511c42a7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242125"
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
 Facultatif. Fichier à ouvrir dans une instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Si aucune instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] n’existe, une instance est créée avec une disposition de fenêtre simplifiée et `file1` est ouvert dans la nouvelle instance.  
  
 `file2`  
 Facultatif. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="remarks"></a>Notes  
 Si aucun fichier n’est spécifié et qu’il existe une instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] reçoit le focus. Si aucun fichier n’est spécifié et qu’il n’y a aucune instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], une instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est créée avec une disposition de fenêtre simplifiée.  
  
 Si l’instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] est dans un état modal, par exemple si la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte, le fichier s’ouvre dans l’instance existante quand [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] quitte l’état modal.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre le fichier `MyFile.cs` dans une instance existante de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou dans une nouvelle instance de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] s’il n’en existe pas déjà une.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)




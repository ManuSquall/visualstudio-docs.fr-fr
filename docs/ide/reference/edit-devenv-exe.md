---
title: -Edit (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05a43cbe880244da1abbb117d23fd928c60da9b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Ouvre le fichier spécifié dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>Arguments  
 `file1`  
 Facultatif. Fichier à ouvrir dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si aucune instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’existe, une instance est créée avec une disposition de fenêtre simplifiée et `file1` est ouvert dans la nouvelle instance.  
  
 `file2`  
 Facultatif. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="remarks"></a>Remarques  
 Si aucun fichier n’est spécifié et qu’il existe une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reçoit le focus. Si aucun fichier n’est spécifié et qu’il n’y a aucune instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est créée avec une disposition de fenêtre simplifiée.  
  
 Si l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est dans un état modal, par exemple si la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte, le fichier s’ouvre dans l’instance existante quand [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quitte l’état modal.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre le fichier `MyFile.cs` dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou dans une nouvelle instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’il n’en existe pas déjà une.  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
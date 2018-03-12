---
title: "Ajout de répertoires à la boîte de dialogue Nouveau projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 881979b54fb8f8f07a7ffeb2f3648b690fe2bf78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Ajout de répertoires à la boîte de dialogue Nouveau projet
Lorsque vous créez de nouveaux types de projet, vous pouvez également inscrire un nouveau répertoire dans le **nouveau projet** boîte de dialogue pour les afficher pour une utilisation en tant que modèles. L’exemple de code suivant explique comment inscrire un nouveau répertoire, également appelé un nœud. Dans l’exemple, les modèles exposées par le VSPackage CLSID_Package sont enregistrés. Par conséquent, le côté gauche de la **nouveau projet** boîte de dialogue donne le nœud ajouté, avec un nom déterminé par la ressource Folder_Label_ResID. Cette ressource est chargée à partir de la DLL du VSPackage satellite.  
  
 Le **dossier** valeur représente un GUID d’un dossier sous lequel le nœud Folder_Label_ResID s’affiche. Dans l’exemple, le GUID représente le **autres projets** dossier dans le **Types de projets** volet de la **nouveau projet** boîte de dialogue. Si le **autres projets** valeur est absente, l’étiquette est positionnée au niveau supérieur.  
  
 La valeur TemplatesDir Spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces fichiers peuvent être des fichiers .vsz ou des fichiers de modèle standard à cloner.  
  
 Si vous spécifiez TemplatesLocalizedSubDir, il doit être l’ID de ressource d’une chaîne qui désigne le sous-répertoire de TemplatesDir qui contient les modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de chaîne à partir d’une DLL satellite si vous en avez, chaque DLL satellite peut contenir un nom de sous-répertoire différents. La valeur SortPriority spécifie un ordre de priorité.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’inscription des modèles de projet et élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Ajouter un élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
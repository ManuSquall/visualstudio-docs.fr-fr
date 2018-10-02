---
title: Ajout de répertoires à la boîte de dialogue Nouveau projet | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e22f0566ddde7bfd795bb01141deabbecd532a19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507426"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Ajout de répertoires à la boîte de dialogue Nouveau projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Ajout de répertoires à la boîte de dialogue Nouveau projet](https://docs.microsoft.com/visualstudio/extensibility/internals/adding-directories-to-the-new-project-dialog-box).  
  
Lorsque vous créez de nouveaux types de projet, vous pouvez également inscrire un nouveau répertoire dans le **nouveau projet** boîte de dialogue pour les afficher pour une utilisation en tant que modèles. L’exemple de code suivant explique comment inscrire un nouveau répertoire, également appelé un nœud. Dans l’exemple, les modèles exposés par le VSPackage CLSID_Package sont enregistrés. Par conséquent, le côté gauche de la **nouveau projet** boîte de dialogue offre le nœud ajouté, avec un nom déterminé par la ressource Folder_Label_ResID. Cette ressource est chargée à partir de la DLL satellite de VSPackage.  
  
 Le **dossier** valeur représente un GUID d’un dossier sous lequel le nœud Folder_Label_ResID s’affiche. Dans l’exemple, le GUID représente le **autres projets** dossier dans le **Types de projets** volet de la **nouveau projet** boîte de dialogue. Si le **autres projets** valeur est absente, l’étiquette est positionnée au niveau supérieur.  
  
 La valeur TemplatesDir Spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces fichiers peuvent être des fichiers .vsz ou des fichiers de modèle standard à cloner.  
  
 Si vous spécifiez TemplatesLocalizedSubDir, il doit être l’ID de ressource d’une chaîne qui nomme le sous-répertoire de TemplatesDir qui contient des modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge la ressource de chaîne à partir d’une DLL satellite si vous en avez pas, chaque DLL satellite peut contenir un nom de sous-répertoire différents. La valeur SortPriority spécifie un ordre de priorité.  
  
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
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Ajouter un élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)


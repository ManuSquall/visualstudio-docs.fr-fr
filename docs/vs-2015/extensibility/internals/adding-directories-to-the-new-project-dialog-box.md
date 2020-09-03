---
title: Ajout de répertoires à la boîte de dialogue Nouveau projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203880"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Ajout de répertoires à la boîte de dialogue Nouveau projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lorsque vous créez de nouveaux types de projets, vous pouvez également inscrire un nouveau répertoire dans la boîte de dialogue **nouveau projet** pour les afficher pour les utiliser comme modèles. L’exemple de code suivant explique comment inscrire un nouveau répertoire, également appelé nœud. Dans l’exemple, les modèles exposés par VSPackage CLSID_Package sont inscrits. Par conséquent, le côté gauche de la boîte de dialogue **nouveau projet** propose le nœud ajouté, avec un nom déterminé par la ressource Folder_Label_ResID. Cette ressource est chargée à partir de la DLL satellite du VSPackage.  
  
 La valeur de **dossier** représente un GUID d’un dossier sous lequel le nœud Folder_Label_ResID s’affiche. Dans l’exemple, le GUID représente le dossier **autres projets** dans le volet **types de projets** de la boîte de dialogue **nouveau projet** . Si la valeur **other Projects** est absente, l’étiquette est positionnée au niveau supérieur.  
  
 La valeur TemplatesDir spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Il peut s’agir de fichiers. vsz ou de fichiers modèles standard à cloner.  
  
 Si vous spécifiez TemplatesLocalizedSubDir, il doit s’agir de l’ID de ressource d’une chaîne qui nomme le sous-répertoire de TemplatesDir qui contient les modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] charge la ressource de type chaîne à partir d’une DLL satellite, si vous en avez une, chaque DLL satellite peut contenir un nom de sous-répertoire différent. La valeur SortPriority spécifie une priorité de tri.  
  
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
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d’éléments aux boîtes de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Ajouter un élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

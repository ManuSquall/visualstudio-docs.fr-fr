---
title: "Ajout de r&#233;pertoires &#224; la bo&#238;te de dialogue Nouveau projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Boîte de dialogue Nouveau projet, extension"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ajout de r&#233;pertoires &#224; la bo&#238;te de dialogue Nouveau projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque vous créez de nouveaux types de projet, vous pouvez également signaler un nouveau répertoire dans la boîte de dialogue de **Nouveau projet** pour les afficher à utiliser comme modèles.  L'exemple de code suivant explique comment inscrire un nouveau répertoire, également connu sous le nœud.  Dans l'exemple, les modèles exposés par VSPackage CLSID\_Package sont enregistrés.  Par conséquent, le côté gauche de la boîte de dialogue de **Nouveau projet** offre le nœud ajouté, avec un nom déterminé par ressource en Folder\_Label\_ResID.  Cette ressource est chargée de la DLL satellites de VSPackage.  
  
 La valeur de **Folder** représente le GUID d'un dossier sous lequel le nœud de Folder\_Label\_ResID s'affiche.  Dans l'exemple, un GUID représente le dossier de **D'autres projets** dans le volet de **Types de projets** de la boîte de dialogue de **Nouveau projet** .  si la valeur de **D'autres projets** est absente, le nom est positionné au niveau supérieur.  
  
 La valeur de TemplatesDir spécifie le chemin d'accès complet du répertoire qui contient les modèles de projet.  Ces fichiers peuvent être des fichiers .vsz ou des fichiers modèles standard à cloner.  
  
 Si vous spécifiez TemplatesLocalizedSubDir, il doit être l'ID de ressource d'une chaîne qui nomme le sous\-répertoire de TemplatesDir qui contient les modèles localisés.  Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de type chaîne d'une DLL satellite si vous avez un, chaque DLL satellite peut contenir un nom différent de sous\-répertoires. la valeur de SortPriority spécifie une priorité de tri.  
  
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
  
## Voir aussi  
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d'éléments à l'ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Nouvel élément Ajouter](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
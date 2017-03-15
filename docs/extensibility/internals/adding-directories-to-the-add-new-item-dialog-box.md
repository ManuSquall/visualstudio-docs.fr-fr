---
title: "Ajout de r&#233;pertoires &#224; la bo&#238;te de dialogue Nouvel &#233;l&#233;ment Ajouter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ajouter un nouvel élément de boîte de dialogue, extension"
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Ajout de r&#233;pertoires &#224; la bo&#238;te de dialogue Nouvel &#233;l&#233;ment Ajouter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L’exemple de code suivant montre comment inscrire un nouvel ensemble de répertoires pour les **Ajouter un nouvel élément** boîte de dialogue. Répertoires pour la **Ajouter un nouvel élément** boîte de dialogue sont différents pour chaque projet. Par conséquent, les répertoires sont enregistrés sous la sous-clé de projets, dans \< HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects > :  
  
## <a name="the-registry-script"></a>Le Script de Registre  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 La valeur Template_Path Spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces modèles peuvent être des fichiers .vsz ou des fichiers de modèle de prototype à cloner.  
  
 La valeur SortPriority indique un ordre de priorité.  
  
## <a name="adding-items-to-an-existing-project"></a>Ajout d’éléments à un projet existant  
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, pour un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet, vous pouvez ajouter des éléments à la \< racine>\VC#\CSharpProjectItems\LocalProjectItems dossier Program Files\Microsoft Visual Studio. Dans ce cas la `%GUID_Project%` est le GUID pour un projet c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Vous pouvez également étendre un projet existant en un sous-type de projet de programmation. Avec un sous-type de projet, vous pouvez étendre un projet sans avoir à écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projets, consultez [sous-types de projets](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’inscription de projet et modèles d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d’éléments à l’ajouter un nouvel élément boîtes de dialogue](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
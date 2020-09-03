---
title: Ajout de répertoires à la boîte de dialogue Ajouter un nouvel élément | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203926"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Ajout de répertoires à la boîte de dialogue Ajouter un élément
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’exemple de code suivant montre comment inscrire un nouvel ensemble de répertoires pour la boîte de dialogue **Ajouter un nouvel élément** . Les répertoires de la boîte de dialogue **Ajouter un nouvel élément** sont différents pour chaque projet. Par conséquent, les répertoires sont inscrits sous la sous-clé de projets, qui se trouve dans \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Le script de Registre  
  
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
  
 La valeur Template_Path spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces modèles peuvent être des fichiers. vsz ou des fichiers de modèles prototypes à cloner.  
  
 La valeur SortPriority spécifie une priorité de tri.  
  
## <a name="adding-items-to-an-existing-project"></a>Ajout d’éléments à un projet existant  
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, pour un [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projet, vous pouvez ajouter des éléments au \<root> dossier \Program Files\Microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems. Dans ce cas, `%GUID_Project%` est le GUID d’un projet C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Vous pouvez également étendre un projet existant en programmant un sous-type de projet. Avec un sous-type de projet, vous pouvez étendre un projet sans écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projet, consultez sous- [types de projet](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Inscription de modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Ajout d’éléments aux boîtes de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Ajout de répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

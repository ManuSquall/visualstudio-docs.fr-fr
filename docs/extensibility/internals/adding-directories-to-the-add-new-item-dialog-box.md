---
title: Ajout de répertoires à la boîte de dialogue Ajouter un nouvel élément | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710253"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément
L’exemple de code suivant montre comment inscrire un nouvel ensemble de répertoires pour la boîte de dialogue **Ajouter un nouvel élément** . Les répertoires de la boîte de dialogue **Ajouter un nouvel élément** sont différents pour chaque projet. Par conséquent, les répertoires sont inscrits sous la sous-clé **projects** , qui se trouve dans **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp\projects**.

## <a name="registry-script"></a>Script du Registre

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

 La `%Template_Path%` valeur spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces modèles peuvent être des fichiers *. vsz* ou des fichiers de modèles prototypes à cloner.

 La `SortPriority` valeur spécifie une priorité de tri.

## <a name="add-items-to-an-existing-project"></a>Ajouter des éléments à un projet existant
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, pour un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet, vous pouvez ajouter des éléments au dossier * \<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . Dans ce cas, `%GUID_Project%` est le GUID d’un projet C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Vous pouvez également étendre un projet existant en programmant un sous-type de projet. Avec un sous-type de projet, vous pouvez étendre un projet sans écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projet, consultez sous- [types de projet](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Voir aussi
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

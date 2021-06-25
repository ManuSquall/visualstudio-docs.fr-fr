---
title: Ajout de répertoires à la boîte de dialogue Ajouter un nouvel élément | Microsoft Docs
description: Découvrez comment ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément dans Visual Studio à l’aide d’un script de Registre pour inscrire les répertoires.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904358"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément
L’exemple de code suivant montre comment inscrire un nouvel ensemble de répertoires pour la boîte de dialogue **Ajouter un nouvel élément** . Les répertoires de la boîte de dialogue **Ajouter un nouvel élément** sont différents pour chaque projet. Par conséquent, les répertoires sont inscrits sous la sous-clé **projects** , qui se trouve dans **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

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
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, pour un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projet, vous pouvez ajouter des éléments au dossier *\<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . Dans ce cas, `%GUID_Project%` est le GUID d’un projet C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Vous pouvez également étendre un projet existant en programmant un sous-type de projet. Avec un sous-type de projet, vous pouvez étendre un projet sans écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projet, consultez sous- [types de projet](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Voir aussi
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

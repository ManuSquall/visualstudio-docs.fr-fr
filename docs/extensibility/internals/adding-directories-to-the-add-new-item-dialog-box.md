---
title: Ajout d’annuaires à la boîte de dialogue d’ajouter un nouvel article (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710253"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Add New Item
L’exemple de code suivant montre comment enregistrer un nouvel ensemble d’annuaires pour la boîte de dialogue **Add New Item.** Les répertoires de la boîte de dialogue **Add New Item** sont différents pour chaque projet. Par conséquent, les répertoires sont enregistrés dans le cadre de la sous-clé **projets,** trouvés dans **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp-Projets**.

## <a name="registry-script"></a>Script de registre

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

 La `%Template_Path%` valeur spécifie le parcours complet de l’annuaire qui contient les modèles de projet. Ces modèles peuvent être soit des fichiers *.vsz* ou des fichiers de modèle prototypique à cloner.

 La `SortPriority` valeur spécifie une priorité de tri.

## <a name="add-items-to-an-existing-project"></a>Ajouter des éléments à un projet existant
 Vous pouvez également ajouter des éléments à un projet existant. Par exemple, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] pour un projet, vous pouvez ajouter des éléments à la * \<racine>-Program Files-Microsoft Visual Studio-CSharpProjectItems -LocalProjectItems* dossier. Dans ce `%GUID_Project%` cas, est le GUID pour un projet C '(FAE04EC0-301F-11D3-BF4B-00C04F79EFBC).

 Vous pouvez également étendre un projet existant en programmant un sous-type de projet. Avec un sous-type de projet, vous pouvez étendre un projet sans écrire un nouveau type de projet. Pour plus d’informations sur les sous-types de projets, voir [sous-types de projet .](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Voir aussi
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue du nouveau projet](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

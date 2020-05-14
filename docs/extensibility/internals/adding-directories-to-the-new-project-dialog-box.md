---
title: Ajout d’annuaires à la nouvelle boîte de dialogue du projet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710247"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue du nouveau projet
Lorsque vous créez de nouveaux types de projets, vous pouvez également enregistrer un nouvel annuaire dans la boîte de dialogue **New Project** pour les afficher pour les utiliser comme modèles. L’exemple de code suivant explique comment enregistrer un nouvel annuaire, également connu sous le nom de nœud. Dans l’exemple, les modèles exposés par le VSPackage, *CLSID_Package*, sont enregistrés. En conséquence, le côté gauche de la boîte de dialogue **New Project** offre le nœud ajouté, avec un nom déterminé par la *ressource Folder_Label_ResID.* Cette ressource est chargée à partir du satellite VSPackage DLL.

 La valeur **du dossier** représente un GUID d’un dossier sous lequel le *nœud Folder_Label_ResID* est affiché. Dans l’exemple, le GUID représente le dossier **Autres Projets** dans le volet **Types de projet** de la boîte de dialogue du nouveau **projet.** Si la valeur **des autres projets** est absente, l’étiquette est positionnée au plus haut niveau.

 La `TemplatesDir` valeur spécifie le parcours complet de l’annuaire qui contient les modèles de projet. Ces fichiers peuvent être soit des fichiers *.vsz* ou des fichiers de modèle typiques à cloner.

 Si vous `TemplatesLocalizedSubDir`spécifiez, il doit être l’ID `TemplatesDir` de ressource d’une chaîne qui nomme la sous-direction de qui contient des modèles localisés. Parce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que charge la ressource de chaîne à partir d’un satellite DLL si vous en avez un, chaque satellite DLL peut contenir un nom sous-directional différent. La `SortPriority` valeur spécifie une priorité de tri.

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
- [Enregistrer les modèles de projets et d’objets](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Add New Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

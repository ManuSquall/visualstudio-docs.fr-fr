---
title: Ajout de répertoires à la boîte de dialogue Nouveau projet | Microsoft Docs
description: Découvrez comment ajouter des répertoires à la boîte de dialogue Nouveau projet dans Visual Studio, afin de pouvoir créer des types de projet et les afficher pour les utiliser comme modèles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901836"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Nouveau projet
Lorsque vous créez de nouveaux types de projets, vous pouvez également inscrire un nouveau répertoire dans la boîte de dialogue **nouveau projet** pour les afficher pour les utiliser comme modèles. L’exemple de code suivant explique comment inscrire un nouveau répertoire, également appelé nœud. Dans l’exemple, les modèles exposés par le VSPackage, *CLSID_Package*, sont inscrits. Par conséquent, le côté gauche de la boîte de dialogue **nouveau projet** propose le nœud ajouté, avec un nom déterminé par la ressource *Folder_Label_ResID* . Cette ressource est chargée à partir de la DLL satellite du VSPackage.

 La valeur de **dossier** représente un GUID d’un dossier sous lequel le nœud *Folder_Label_ResID* s’affiche. Dans l’exemple, le GUID représente le dossier **autres projets** dans le volet **types de projets** de la boîte de dialogue **nouveau projet** . Si la valeur **other Projects** est absente, l’étiquette est positionnée au niveau supérieur.

 La `TemplatesDir` valeur spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Il peut s’agir de fichiers *. vsz* ou de fichiers modèles standard à cloner.

 Si vous spécifiez `TemplatesLocalizedSubDir` , il doit s’agir de l’ID de ressource d’une chaîne qui nomme le sous-répertoire de `TemplatesDir` qui contient les modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de type chaîne à partir d’une DLL satellite, si vous en avez une, chaque DLL satellite peut contenir un nom de sous-répertoire différent. La `SortPriority` valeur spécifie une priorité de tri.

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
- [Inscrire des modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

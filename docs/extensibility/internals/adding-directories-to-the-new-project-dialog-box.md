---
title: Ajout de répertoires à la boîte de dialogue Nouveau projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e81d09c2a4e97ca5f3da112e593b04b219e6314
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328002"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Ajouter des répertoires à la boîte de dialogue Nouveau projet
Lorsque vous créez de nouveaux types de projet, vous pouvez également inscrire un nouveau répertoire dans le **nouveau projet** boîte de dialogue pour les afficher pour une utilisation en tant que modèles. L’exemple de code suivant explique comment inscrire un nouveau répertoire, également appelé un nœud. Dans l’exemple, les modèles exposés par le VSPackage, *CLSID_Package*, sont inscrits. Par conséquent, le côté gauche de la **nouveau projet** boîte de dialogue offre le nœud ajouté, avec un nom déterminé par le *Folder_Label_ResID* ressource. Cette ressource est chargée à partir de la DLL satellite de VSPackage.

 Le **dossier** valeur représente un GUID d’un dossier sous lequel le *Folder_Label_ResID* nœud s’affiche. Dans l’exemple, le GUID représente le **autres projets** dossier dans le **Types de projets** volet de la **nouveau projet** boîte de dialogue. Si le **autres projets** valeur est absente, l’étiquette est positionnée au niveau supérieur.

 Le `TemplatesDir` valeur spécifie le chemin d’accès complet du répertoire qui contient les modèles de projet. Ces fichiers peuvent être soit *.vsz* fichiers ou des fichiers de modèle standard à cloner.

 Si vous spécifiez `TemplatesLocalizedSubDir`, il doit être l’ID de ressource d’une chaîne qui nomme le sous-répertoire de `TemplatesDir` qui contient des modèles localisés. Étant donné que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] charge la ressource de chaîne à partir d’une DLL satellite si vous en avez pas, chaque DLL satellite peut contenir un nom de sous-répertoire différents. Le `SortPriority` valeur spécifie un ordre de priorité.

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
- [Inscrire les modèles de projet et d’élément](../../extensibility/internals/registering-project-and-item-templates.md)
- [Ajouter des éléments à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Ajouter des répertoires à la boîte de dialogue Ajouter un nouvel élément](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
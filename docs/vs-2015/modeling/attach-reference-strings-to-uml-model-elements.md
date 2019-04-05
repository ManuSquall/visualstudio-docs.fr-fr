---
title: Attacher des chaînes de référence à des éléments de modèle UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5a1ae4abc2e0b5c508b7b77160bbf8da3bb45e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948374"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Attacher des chaînes de référence à des éléments de modèle UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez écrire du code pour attacher des chaînes arbitraires à des éléments de modèle. Une chaîne peut être, par exemple, un URI, le résultat mis en cache d'un calcul ou une référence ModelBus à un élément dans un autre modèle. Chaque chaîne est contenue dans un objet IReference. Un nombre quelconque d'objets IReference peut être attaché à chaque élément de modèle.  
  
 Chaque objet IReference a un nom. Vous pouvez utiliser ce nom pour indiquer comment la valeur de référence doit être interprétée. Par exemple, vous pouvez définir le nom « URI » pour indiquer que la valeur doit être interprétée comme un URI. Il existe certaines valeurs de noms de référence prédéfinies utilisées par les outils de modélisation.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Attachement d'une référence à un IElement  
 Pour utiliser les méthodes suivantes, vous devez ajouter une référence à :  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 Vous devez insérer cette directive dans votre code :  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Appel de méthode|Description|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Crée un `IReference` avec les chaînes de nom et de valeur données et le lie à `element`. Retourne l'`IReference`.<br /><br /> Lève une exception si `duplicatesAllowed` a la valeur false et qu'il existe déjà un `IReference` du même nom attaché à `element`.|  
|`element.GetReferences(name)`|Retourne tous les objets `IReference` liés à `element` qui ont le `name` donné.|  
|`element.DeleteAllReferences(name)`|Supprime tous les objets `IReference` liés à l'élément qui ont le nom donné.|  
|`reference.Delete()`|Supprime ce `IReference`.|  
|`ReferenceConstants.WorkItem`|Valeur utilisée pour nommer les références aux éléments de travail.|  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un gestionnaire de liaison des éléments de travail](../modeling/define-a-work-item-link-handler.md)   
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)

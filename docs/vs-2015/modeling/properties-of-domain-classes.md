---
title: Propriétés des Classes de domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c668317fba69100701fac95bfa333ed7b3446488
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701964"
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [présentation des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<aucune>|  
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la classe de domaine (`none`, `abstract` ou `sealed`).|`none`|  
|Classe de base|Si cette classe de domaine est dérivée, le nom de la classe de base.|\<aucune>|  
|Nom|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms de cette classe de domaine.|Espace de noms actuel|  
|Notes|Remarques informelles associées à cette classe de domaine.|\<aucune>|  
|Description|La description est utilisée pour documenter l’interface utilisateur du concepteur généré.|\<aucune>|  
|Display Name|Le nom qui s’affichera dans le concepteur généré pour cette classe de domaine.|\<aucune>|  
|Help Keyword|Le mot clé facultatif qui est utilisé pour indexer l’aide F1 pour cette classe de domaine.|\<aucune>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

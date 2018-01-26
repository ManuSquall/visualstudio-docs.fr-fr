---
title: "Propriétés des Classes de domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f6e7310f88b4c5f0855a6851219727ae0dc82d86
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
Classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [fonctionnement des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Default|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<none>|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la classe de domaine (`none`, `abstract` ou `sealed`).|`none`|  
|Classe de base|Si cette classe de domaine est dérivée, le nom de la classe de base.|\<none>|  
|Nom|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms de cette classe de domaine.|Espace de noms actuel|  
|Remarques|Notes informelles qui sont associés à cette classe de domaine.|\<none>|  
|Description|La description qui est utilisée pour l’interface utilisateur du concepteur généré de document.|\<none>|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<none>|  
|Help Keyword|Le mot clé facultatif qui sert à l’index d’aide (F1) pour cette classe de domaine.|\<none>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
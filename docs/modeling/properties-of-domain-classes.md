---
title: "Propriétés des Classes de domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e38000dea9c20f8458fd0f899d43ea8f7c9eb7db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-domain-classes"></a>Propriétés des classes de domaine
Classes de domaine ont les propriétés dans le tableau suivant. Pour plus d’informations sur les classes de domaine, consultez [fonctionnement des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Niveau d'accès de la classe de domaine (`public` ou `internal`).|`public`|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de cette classe de domaine.|\<Aucun >|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) seront générés. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A constructeur personnalisé|Si `True`, un constructeur personnalisé sera fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la classe de domaine (`none`, `abstract` ou `sealed`).|`none`|  
|Classe de base|Si cette classe de domaine est dérivée, le nom de la classe de base.|\<Aucun >|  
|Name|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms de cette classe de domaine.|Espace de noms actuel|  
|Notes|Notes informelles qui sont associés à cette classe de domaine.|\<Aucun >|  
|Description|La description qui est utilisée pour l’interface utilisateur du concepteur généré de document.|\<Aucun >|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<Aucun >|  
|Help Keyword|Le mot clé facultatif qui sert à l’index d’aide (F1) pour cette classe de domaine.|\<Aucun >|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
---
title: "Propri&#233;t&#233;s des relations de domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Langage spécifique à un domaine, relations de domaine"
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Propri&#233;t&#233;s des relations de domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les propriétés dans le tableau suivant sont associées à une relation de domaine. Pour plus d’informations sur les relations de domaine, consultez [fonctionnement des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique au domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Le niveau d’accès de la relation de domaine (`public` ou `internal`).|`public`|  
|Attributs personnalisés|Permet d’ajouter des attributs à la classe de code source qui est générée à partir de la relation de domaine.|\< aucun>|  
|Génère les deux dérivées|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via les remplacements) est générée. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A le constructeur personnalisé|Si `True`, indique qu’un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la relation de domaine (`none`, `abstract` ou `sealed`).|\< aucun>|  
|Autorise les doublons|Si `True`, des liens en double de la relation de domaine peuvent être créés entre les deux mêmes éléments.|`False`|  
|Relations de base|Si la relation de domaine est dérivée, la relation de la base de la relation de domaine.|\< aucun>|  
|Est l’incorporation|Si `True`, la relation de domaine est une relation d’incorporation. Si `False`, la relation est une relation de référence.|\< à la fois>|  
|Nom|Le nom de la relation de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms qui est lié à la relation de domaine.|Espace de noms actuel|  
|Notes|Remarques informelles associées à la relation de domaine.|\< aucun>|  
|Description|La description qui est utilisée pour documenter du code et est utilisée dans l’interface Utilisateur du concepteur généré.|\< aucun>|  
|Nom complet|Le nom qui s’affiche dans le concepteur généré pour la relation de domaine.|\< aucun>|  
|Mot clé d’aide|Le mot clé facultatif qui est utilisé pour indexer l’aide F1 pour la relation de domaine.|\< aucun>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)
---
title: "Propriétés d’une définition DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
Définissent les propriétés DslDefinition *langage spécifique au domaine* propriétés telles que la numérotation des versions de la définition. Les propriétés DslDefinition s’affichent dans le **propriétés** fenêtre lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur de langage spécifique à un domaine*.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique au domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique au domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition a les propriétés dans le tableau suivant :  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Détermine si le modificateur d’accès pour la classe de domaine public ou interne.|public|  
|Attributs personnalisés|Custom attributs définis pour la classe de domaine.<br /><br /> **Remarque** utiliser le bouton Parcourir pour ajouter un attribut.|\<Aucun >|  
|Nom de la société|Le nom de la société actuelle dans le Registre système.|Nom de la société|  
|Nom|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms affilié à cette classe de domaine.|Espace de noms actuel|  
|Guid du package|Le guid pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette solution DSL.|\<Aucun >|  
|Package Namespace|L’espace de noms pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette solution DSL.|\<Aucun >|  
|Nom du produit|Le nom du produit qui est enregistré pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette solution DSL.|\<Aucun >|  
|Notes|Notes associées à cette classe de domaine.|\<Aucun >|  
|Description|Description de cette classe de domaine.|\<Aucun >|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<Aucun >|  
|Help Keyword|Le mot clé d’aide associé à cette classe de domaine.|\<Aucun >|  
|Build|Numéro de build incrémentielle pour cette définition de langage spécifique au domaine.|0|  
|Version principale|Numéro de build majeur incrémentielle pour cette définition de langage spécifique au domaine.|1|  
|Version secondaire|Numéro de version mineure incrémentielle pour cette définition de langage spécifique au domaine.|0|  
|Révision|La révision incrémentiel numéro de build pour cette définition de langage spécifique au domaine.|0|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)

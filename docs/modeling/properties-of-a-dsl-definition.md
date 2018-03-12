---
title: "Propriétés d’une définition DSL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5ccf6937aa3c317feb81a907348d41e4d322d346
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
Définissent des propriétés de DslDefinition *langage spécifique à un domaine* propriétés telles que la numérotation des versions de la définition. Les propriétés de DslDefinition s’affichent dans le **propriétés** fenêtre lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur de langage spécifique à un domaine*.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition a les propriétés dans le tableau suivant :  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Détermine si le modificateur d’accès pour la classe de domaine est public ou interne.|public|  
|Attributs personnalisés|Custom attributs définis pour la classe de domaine.<br /><br /> **Remarque** utiliser le bouton Parcourir pour ajouter un attribut.|\<none>|  
|Nom de la société|Le nom du nom de la société actuelle dans le Registre système.|Nom de la société|  
|Name|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms affilié à cette classe de domaine.|Espace de noms actuel|  
|Guid du package|Le guid pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette DSL.|\<none>|  
|Package Namespace|L’espace de noms pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette DSL.|\<none>|  
|Nom du produit|Le nom du produit qui sera inscrit pour le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] package généré pour cette DSL.|\<none>|  
|Notes|Notes associées à cette classe de domaine.|\<none>|  
|Description|Description pour cette classe de domaine.|\<none>|  
|Nom complet|Le nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<none>|  
|Help Keyword|Le mot clé d’aide associé à cette classe de domaine.|\<none>|  
|Générer|Numéro de build incrémentielle pour cette définition de langage spécifique à un domaine.|0|  
|Version principale|Le numéro de build majeur incrémentielle pour cette définition de langage spécifique à un domaine.|1|  
|Version mineure|Le numéro de build mineure incrémentielle pour cette définition de langage spécifique à un domaine.|0|  
|Révision|La révision incrémentiel numéro de build pour cette définition de langage spécifique à un domaine.|0|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
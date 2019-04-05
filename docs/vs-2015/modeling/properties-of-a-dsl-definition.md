---
title: Propriétés d’une définition DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 804236cadf97dda0b21cf145a4cd4c932e08b097
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953189"
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définissent les propriétés DslDefinition *langage spécifique à un domaine* propriétés telles que la numérotation des versions de la définition. Les propriétés DslDefinition s’affichent dans le **propriétés** fenêtre lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur de langage spécifique à un domaine*.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition a les propriétés dans le tableau suivant :  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Détermine si le modificateur d’accès pour la classe de domaine est public ou interne.|public|  
|Attributs personnalisés|Custom attributs définis pour la classe de domaine.<br /><br /> **Remarque** utilisez le bouton Parcourir pour ajouter un attribut.|\<aucune>|  
|Nom de la société|Le nom du nom de la société actuelle dans le Registre système.|Nom de la société|  
|Nom|Le nom de cette classe de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms affilié à cette classe de domaine.|Espace de noms actuel|  
|Guid du package|Le guid pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<aucune>|  
|Package Namespace|L’espace de noms pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<aucune>|  
|Nom du produit|Le nom du produit qui sera inscrit pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<aucune>|  
|Notes|Notes associées à cette classe de domaine.|\<aucune>|  
|Description|Description de cette classe de domaine.|\<aucune>|  
|Display Name|Le nom qui s’affichera dans le concepteur généré pour cette classe de domaine.|\<aucune>|  
|Help Keyword|Le mot clé d’aide associé à cette classe de domaine.|\<aucune>|  
|Build|Numéro de build incrémentielle de cette définition de langage spécifique à un domaine.|0|  
|Version majeure|Le numéro de build majeur incrémentielle pour cette définition de langage spécifique à un domaine.|1|  
|Version mineure|Le numéro de build mineure incrémentielle pour cette définition de langage spécifique à un domaine.|0|  
|Revision|La révision incrémentiel numéro de build pour cette définition de langage spécifique à un domaine.|0|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des Outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

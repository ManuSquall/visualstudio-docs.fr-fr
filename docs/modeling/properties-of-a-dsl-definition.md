---
title: Propriétés d'une définition DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9ee2f0e2353023f1864c892ecc377050ea87923d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865412"
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
Définissent les propriétés DslDefinition *langage spécifique à un domaine* propriétés telles que la numérotation des versions de la définition. Les propriétés DslDefinition s’affichent dans le **propriétés** fenêtre lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur de langage spécifique à un domaine*.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition a les propriétés dans le tableau suivant :

|Propriété|Description|Par défaut|
|-|-|-|
|Modificateur d'accès|Détermine si le modificateur d’accès pour la classe de domaine est public ou interne.|public|
|Attributs personnalisés|Custom attributs définis pour la classe de domaine.<br /><br /> **Remarque** utilisez le bouton Parcourir pour ajouter un attribut.|\<Aucun >|
|Nom de la société|Le nom du nom de la société actuelle dans le Registre système.|Nom de la société|
|Name|Le nom de cette classe de domaine.|Nom actuel|
|Espace de noms|L’espace de noms affilié à cette classe de domaine.|Espace de noms actuel|
|Guid du package|Le guid pour le package Visual Studio généré pour ce DSL.|\<Aucun >|
|Package Namespace|L’espace de noms pour le package Visual Studio généré pour ce DSL.|\<Aucun >|
|Nom du produit|Le nom du produit qui sera inscrit pour le package Visual Studio généré pour ce DSL.|\<Aucun >|
|Notes|Notes associées à cette classe de domaine.|\<Aucun >|
|Description|Description de cette classe de domaine.|\<Aucun >|
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour cette classe de domaine.|\<Aucun >|
|Help Keyword|Le mot clé d’aide associé à cette classe de domaine.|\<Aucun >|
|Build|Numéro de build incrémentielle de cette définition de langage spécifique à un domaine.|0|
|Version majeure|Le numéro de build majeur incrémentielle pour cette définition de langage spécifique à un domaine.|1|
|Version mineure|Le numéro de build mineure incrémentielle pour cette définition de langage spécifique à un domaine.|0|
|Révision|La révision incrémentiel numéro de build pour cette définition de langage spécifique à un domaine.|0|

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
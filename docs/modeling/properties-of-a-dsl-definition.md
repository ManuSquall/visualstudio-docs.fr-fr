---
title: Propriétés d'une définition DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c7ff2be87a91e6c01ec275bcff1d77aa6481df1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658277"
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
Les propriétés DslDefinition définissent des propriétés de définition du *langage spécifique à un domaine* , telles que la numérotation des versions. Les propriétés DslDefinition s’affichent dans la fenêtre **Propriétés** lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur Domain-specific language*.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition possède les propriétés dans le tableau suivant :

|Property|Description|Valeur par défaut|
|-|-|-|
|Modificateur d'accès|Détermine si le modificateur d’accès pour la classe de domaine est public ou Internal.|public|
|Attributs personnalisés|Attributs définis personnalisés pour la classe de domaine.<br /><br /> **Remarque** Utilisez le bouton Parcourir pour ajouter un attribut.|\<aucune>|
|Nom de la société|Nom de la société actuelle dans le registre système.|Nom de la société actuelle|
|Name|Nom de cette classe de domaine.|Nom actuel|
|Espace de noms|Espace de noms affilié à cette classe de domaine.|Espace de noms actuel|
|GUID du package|GUID du package Visual Studio généré pour ce DSL.|\<aucune>|
|Espace de noms du package|Espace de noms du package Visual Studio généré pour ce DSL.|\<aucune>|
|Nom du produit|Nom du produit qui sera inscrit pour le package Visual Studio généré pour ce DSL.|\<aucune>|
|Notes|Notes associées à cette classe de domaine.|\<aucune>|
|Description|Description de cette classe de domaine.|\<aucune>|
|Display Name|Nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<aucune>|
|Help Keyword|Mot clé d’aide associé à cette classe de domaine.|\<aucune>|
|Générer|Numéro de build incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Version principale|Numéro de build majeur incrémentiel pour cette définition de langage spécifique à un domaine.|1|
|Version mineure|Numéro de build mineure incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Revision|Numéro de build de révision incrémentielle pour cette définition de langage spécifique à un domaine.|0|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
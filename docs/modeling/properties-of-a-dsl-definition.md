---
title: Propriétés d'une définition DSL
description: Découvrez que les propriétés DslDefinition définissent des propriétés de définition de langage spécifique à un domaine, telles que la numérotation des versions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48771a61577c5c7ca910cc3b4f8496db37ada281
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360518"
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
Les propriétés DslDefinition définissent des propriétés de définition du *langage spécifique à un domaine* , telles que la numérotation des versions. Les propriétés DslDefinition s’affichent dans la fenêtre **Propriétés** lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur Domain-specific language*.

 Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition possède les propriétés dans le tableau suivant :

|Propriété|Description|Default|
|-|-|-|
|Modificateur d'accès|Détermine si le modificateur d'accès pour la classe de domaine est public ou interne.|public|
|Attributs personnalisés|Attributs définis personnalisés pour la classe de domaine.<br /><br /> **Remarque** Utilisez le bouton Parcourir pour ajouter un attribut.|\<none>|
|Nom de la société|Nom de la société actuelle dans le registre système.|Nom de la société actuelle|
|Nom|Nom de cette classe de domaine.|Nom actuel|
|Espace de noms|Espace de noms affilié à cette classe de domaine.|Espace de noms actuel|
|GUID du package|GUID du package Visual Studio généré pour ce langage spécifique à un domaine.|\<none>|
|Espace de noms du package|Espace de noms du package Visual Studio généré pour ce langage spécifique à un domaine.|\<none>|
|Nom du produit|Nom du produit qui sera enregistré pour le package Visual Studio généré pour ce langage spécifique à un domaine.|\<none>|
|Remarques|Notes associées à cette classe de domaine.|\<none>|
|Description|Description de cette classe de domaine.|\<none>|
|Nom complet|Nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<none>|
|Help Keyword|Mot clé d’aide associé à cette classe de domaine.|\<none>|
|Build|Numéro de build incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Version majeure|Numéro de build majeur incrémentiel pour cette définition de langage spécifique à un domaine.|1|
|Version mineure|Numéro de build mineure incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Révision|Numéro de build de révision incrémentielle pour cette définition de langage spécifique à un domaine.|0|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
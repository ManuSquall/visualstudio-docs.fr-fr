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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8755b1b70051c54157fa87ee0b66dbc9340b5024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668466"
---
# <a name="properties-of-a-dsl-definition"></a>Propriétés d'une définition DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les propriétés DslDefinition définissent des propriétés de définition du *langage spécifique à un domaine* , telles que la numérotation des versions. Les propriétés DslDefinition s’affichent dans la fenêtre **Propriétés** lorsque vous cliquez sur une zone ouverte du diagramme dans le *Concepteur Domain-specific language*.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition possède les propriétés dans le tableau suivant :

|Propriété|Description|Default|
|--------------|-----------------|-------------|
|Modificateur d'accès|Détermine si le modificateur d'accès pour la classe de domaine est public ou interne.|public|
|Attributs personnalisés|Attributs définis personnalisés pour la classe de domaine.<br /><br /> **Remarque** Utilisez le bouton Parcourir pour ajouter un attribut.|\<none>|
|Nom de l’entreprise|Nom de la société actuelle dans le registre système.|Nom de la société actuelle|
|Nom|Nom de cette classe de domaine.|Nom actuel|
|Espace de noms|Espace de noms affilié à cette classe de domaine.|Espace de noms actuel|
|GUID du package|GUID du [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<none>|
|Espace de noms du package|Espace de noms pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<none>|
|Nom du produit|Nom du produit qui sera inscrit pour le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] package généré pour ce DSL.|\<none>|
|Notes|Notes associées à cette classe de domaine.|\<none>|
|Description|Description de cette classe de domaine.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour cette classe de domaine.|\<none>|
|Help Keyword|Mot clé d’aide associé à cette classe de domaine.|\<none>|
|Build|Numéro de build incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Version majeure|Numéro de build majeur incrémentiel pour cette définition de langage spécifique à un domaine.|1|
|Version mineure|Numéro de build mineure incrémentiel pour cette définition de langage spécifique à un domaine.|0|
|Révision|Numéro de build de révision incrémentielle pour cette définition de langage spécifique à un domaine.|0|

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

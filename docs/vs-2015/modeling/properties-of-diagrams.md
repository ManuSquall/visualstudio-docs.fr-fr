---
title: Propriétés des diagrammes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652026"
---
# <a name="properties-of-diagrams"></a>Propriétés des diagrammes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir des propriétés qui spécifient le mode d’affichage des diagrammes dans le concepteur généré. Par exemple, vous pouvez spécifier une couleur par défaut pour le texte dans le diagramme.

 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Le tableau suivant répertorie les propriétés des diagrammes.

|Propriété|Description|Default|
|--------------|-----------------|-------------|
|Couleur de remplissage|Couleur de remplissage du diagramme.|White|
|Couleur du texte|Couleur du texte affiché sur le diagramme.|Noir|
|Modificateur d'accès|Modificateur d’accès de la classe (public ou Internal).|Public|
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code générée.|\<none>|
|Génère un doublon dérivé|Si `True` la valeur est, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générées. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|Faux|
|A un constructeur personnalisé|Si `True` , un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|Faux|
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est généré à partir du diagramme ( `none` , `abstract` ou `sealed` ).|None|
|Diagramme de base|Classe de base de ce diagramme.|(aucun)|
|Nom|Nom de ce diagramme.|Nom actuel|
|Espace de noms|Espace de noms affilié à ce diagramme.|Espace de noms actuel|
|Classe représentée|Classe de domaine racine représentée par ce diagramme.|Classe racine actuelle, le cas échéant|
|Notes|Notes informelles associées à cet élément.|\<none>|
|Expose la couleur de remplissage en tant que propriété|Si la `True` valeur est, l’utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré. Pour ce faire, cliquez avec le bouton droit sur la forme du diagramme, puis cliquez sur **Ajouter Explosed**.|Faux|
|Expose la couleur de texte en tant que propriété|Si la `True` valeur est, l’utilisateur peut définir la couleur de texte du diagramme dans le concepteur généré. Pour ce faire, cliquez avec le bouton droit sur la forme du diagramme, puis cliquez sur **Ajouter Explosed**.|Faux|
|Description|Description utilisée pour documenter le concepteur généré.|\<none>|
|Nom d’affichage|Nom qui sera affiché dans le concepteur généré pour ce diagramme.|\<none>|
|Help Keyword|Mot clé utilisé pour indexer l’aide F1 pour ce diagramme.|\<none>|

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

---
title: FxCopCmd (erreurs)
ms.date: 10/19/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34ec1b04e10b874d6f8373b5eb0e6c2e5c6d70e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844078"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd (erreurs) outil

FxCopCmd ne considère pas toutes les erreurs comme irrécupérable. Si FxCopCmd dispose d’informations suffisantes pour effectuer une analyse partielle, il effectue l’analyse et signale les erreurs qui se sont produites. Le code d’erreur, qui est un entier 32 bits, contient une combinaison au niveau du bit des valeurs numériques qui correspondent aux erreurs.

Le tableau suivant décrit les codes d’erreur retournés par FxCopCmd :

|Error|Valeur numérique|
|-----------|-------------------|
|Aucune erreur|0 x 0|
|Erreur d’analyse|0 x 1|
|Exceptions de règle|0 x 2|
|Erreur de chargement de projet|0 x 4|
|Erreur de chargement d’assembly|0 x 8|
|Erreur de chargement de bibliothèque de règle|0x10|
|Erreur de chargement du rapport importation|0 x 20|
|Erreur de sortie|0 x 40|
|Erreur de commutateur de ligne de commande|0 x 80|
|Erreur d’initialisation|0 x 100|
|Erreur des références d’assembly|0 x 200|
|BuildBreakingMessage|0 x 400|
|Erreur inconnue|0x1000000|

**Erreur d’analyse** est retournée pour les erreurs irrécupérables. Il indique que l’analyse a échoué. Le cas échéant, le code d’erreur contient également la cause sous-jacente de l’erreur irrécupérable. Les conditions suivantes génèrent des erreurs irrécupérables :

- L’analyse n’a pas pu être effectuée en raison d’une entrée insuffisante.

- L’analyse a levé une exception non gérée par FxCopCmd.

- Le fichier projet spécifié est introuvable ou est endommagé.

- L’option de sortie n’a pas été spécifiée ou le fichier n’a pas pu être écrites.

> [!NOTE]
> Le code retour FxCopCmd **erreur des références d’Assembly** 0 x 200 en lui-même est un avertissement plutôt qu’une erreur. Ce code de retour indique à qui il manque des références indirectes, mais que FxCopCmd a été en mesure de les gérer. L’avertissement signifie qu’il est possible que certains résultats de l’analyse a été compromises. Traiter **erreur des références d’Assembly** comme une erreur lorsqu’il est combiné avec n’importe quel autre code de retour.

## <a name="see-also"></a>Voir aussi

- [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)
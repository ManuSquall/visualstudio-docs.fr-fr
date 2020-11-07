---
title: FxCopCmd (erreurs)
ms.date: 10/19/2016
description: En savoir plus sur les codes d’erreur renvoyés par la commande FxCopCmd. Déterminez le type d’erreur que représente chaque code et découvrez comment reconnaître les erreurs irrécupérables.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c900ec10ea13e7f9d7092769565703bf52fe8c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348930"
---
# <a name="fxcopcmd-tool-errors"></a>Erreurs de l’outil FxCopCmd

FxCopCmd ne considère pas que toutes les erreurs sont irrécupérables. Si FxCopCmd dispose d’informations suffisantes pour effectuer une analyse partielle, il effectue l’analyse et signale les erreurs qui se sont produites. Le code d’erreur, qui est un entier 32 bits, contient une combinaison d’opérations de bits de valeurs numériques qui correspondent aux erreurs.

Le tableau suivant décrit les codes d’erreur retournés par FxCopCmd :

|Erreur|Valeur numérique|
|-----------|-------------------|
|Aucune erreur|0x0|
|Erreur d’analyse|0x1|
|Exceptions de règle|0x2|
|Erreur de chargement du projet|0x4|
|Erreur de chargement de l’assembly|0x8|
|Erreur de chargement de la bibliothèque de règles|0x10|
|Erreur de chargement du rapport d’importation|0x20|
|Erreur de sortie|0x40|
|Erreur de commutateur de ligne de commande|0x80|
|Erreur d’initialisation|0x100|
|Erreur de références d’assembly|0x200|
|BuildBreakingMessage|0x400|
|Erreur inconnue|0x1000000|

Une **erreur d’analyse** est renvoyée pour les erreurs irrécupérables. Elle indique que l’analyse n’a pas pu être effectuée. Le cas échéant, le code d’erreur contient également la cause sous-jacente de l’erreur irrécupérable. Les conditions suivantes génèrent des erreurs irrécupérables :

- L’analyse n’a pas pu être effectuée en raison d’une entrée insuffisante.

- L’analyse a levé une exception qui n’est pas gérée par FxCopCmd.

- Le fichier projet spécifié est introuvable ou endommagé.

- L’option de sortie n’a pas été spécifiée ou le fichier n’a pas pu être écrit.

> [!NOTE]
> L' **assembly** de code de retour FxCopCmd référence l’erreur 0x200 en lui-même est un avertissement plutôt qu’une erreur. Ce code de retour indique qu’il manque des références indirectes, mais que FxCopCmd a pu les gérer. L’avertissement signifie qu’il est possible que certains résultats d’analyse aient été compromis. Considérer les **références d’assembly** comme une erreur lorsqu’elle est associée à un autre code de retour.

## <a name="see-also"></a>Voir aussi

- [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)

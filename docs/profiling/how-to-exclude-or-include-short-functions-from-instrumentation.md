---
title: Exclure ou inclure les fonctions courtes de l’instrumentation
description: Par défaut, les fonctions courtes qui n’appellent pas d’autres fonctions sont exclues de l’instrumentation pour réduire la surcharge. Découvrez comment les inclure ou les exclure.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ad449ba25e2b97397ae87cfe64eb7253ac5728b7
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800403"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Guide pratique pour exclure ou inclure les fonctions courtes de l’instrumentation
Par défaut, les outils de profilage excluent les *petites fonctions* de l’instrumentation. Les petites fonctions sont des fonctions courtes qui n’effectuent pas d’appels de fonction. L’exclusion de ces petites fonctions permet de réduire la surcharge d’instrumentation, et donc d’accélérer la vitesse d’instrumentation. L’exclusion des petites fonctions réduit également le fichier de données de profilage des performances (.*vsp*) et le temps requis pour l’analyse. Si les petites fonctions sont exclues, le temps qui leur est consacré sera soustrait du temps exclusif et inclusif de leurs fonctions parents. Les petites fonctions peuvent être exclues ou incluses dans l’instrumentation, comme le décrit la procédure suivante.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Pour exclure ou inclure les fonctions courtes de l’instrumentation

1. Dans l’**Explorateur de performances**, sélectionnez **Session de performance**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.

     La boîte de dialogue **Pages de propriétés** s’affiche.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Instrumentation**.

3. Pour exclure les fonctions courtes de l’instrumentation, sélectionnez **Exclure les petites fonctions de l’instrumentation**. Il s'agit du paramètre par défaut.

     -ou-

     Pour inclure les fonctions courtes dans l’instrumentation, décochez la case **Exclure les petites fonctions de l’instrumentation**.

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
- [Contrôler la collecte des données](../profiling/controlling-data-collection.md)
- [Propriétés d’une session de performance](../profiling/performance-session-properties.md)

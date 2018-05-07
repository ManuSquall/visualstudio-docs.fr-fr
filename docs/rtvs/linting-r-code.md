---
title: Vérification (linting) du code R
description: Guide pratique pour travailler avec la prise en charge pour R du linting intégré de Visual Studio, y compris les options de linting.
ms.date: 01/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: e5494283fdf759ddc664207d62d40f7f83993632
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Linting de code R dans Visual Studio

Le linting (ou vérification lint) analyse le code pour révéler des erreurs potentielles, des problèmes de mise en forme et d’autres parasites dans le code, par exemple un faux espace blanc. Le linting contribue également à encourager certaines conventions de codage, telles que la manière de nommer les identificateurs. Ces conventions sont utiles au sein d’équipes et dans d’autres situations de collaboration.

Outils R pour Visual Studio (RTVS) fournit un linting intégré pour R, dont le comportement est contrôlé par le biais de diverses options décrites dans cet article. Ces options sont trouvent dans **Outils > Options > Éditeur de texte > R > Lint**.

Le linting est désactivé par défaut. Pour activer le linting, affectez à l’option **Tout > Activer lint** la valeur true.

Quand il est activé, le linting s’applique dans l’éditeur pendant la frappe. Les problèmes sont signalés par des lignes ondulées vertes. Dans le graphique suivant, par exemple, RTVS a identifié six problèmes de linting, notamment l’utilisation de `=` au lieu de `<-` pour une assignation, un manque d’espace autour d’arguments de fonction, l’utilisation de la casse Pascal et d’identificateurs en majuscules, ainsi que l’utilisation d’un point-virgule. Pointez le curseur sur un problème pour afficher une description.

![Exemples de linting pour du code R](media/linting-01.png)

Souvent, vous modifiez les options de linting selon les besoins d’un projet ou d’un fichier. Par exemple, un code provenant d’un cours en ligne peut utiliser `=` au lieu de `<-` , ainsi que des identificateurs à casse Pascal. Un tel code affiche de fréquents avertissements de linting car les options de linting par défaut signalent ces cas. Lorsque vous utilisez ce code, vous pouvez désactiver les options au lieu de perdre du temps à corriger chaque instance.

## <a name="assignment-group"></a>Groupe d’assignation

| Option | Valeur par défaut | Effet de linting |
| --- | --- | --- |
| Appliquer \<- | `True` | Détecte si `<-` n’est pas utilisé pour l’assignation. |

## <a name="naming-group"></a>Groupe de nommage

Ces options marquent des identificateurs qui utilisent des conventions de nommage différentes :

| Option | Valeur par défaut | Effet de linting |
| --- | --- | --- |
| Marquer la casse mixte | `False` | Marque les identificateurs qui utilisent une casse mixte. |
| Marquer les noms longs | `False` | Marque les identificateurs dont le nom dépasse le paramètre « Longueur maximale de nom ». |
| Marquer plusieurs points | `True` | Marque les identificateurs qui utilisent plusieurs points. |
| Marquer la casse Pascal | `True` | Marque les identificateurs qui utilisent la casse Pascal. |
| Marquer les mots séparés par des tirets | `False` | Marque les identificateurs qui utilisent des traits de soulignements. |
| Marquer les majuscules | `True` | Marque les identificateurs qui n’utilisent que des majuscules. |
| Longueur maximale de nom | 32 | Longueur appliquée avec le paramètre « Marquer les noms longs ». |

## <a name="spacing-group"></a>Groupe d’espacement

Ces options, qui ont toutes la valeur `True` par défaut, contrôlent l’endroit où le linting identifie les problèmes d’espacement : après les noms de fonctions, autour des virgules, autour des opérateurs, aux positions des accolades ouvrantes et fermantes, à l’espace précédent ( et à l’espace à l’intérieur de ().

## <a name="statements-group"></a>Groupe d’instructions

| Option | Valeur par défaut | Effet de linting |
| --- | --- | --- |
| Multiple | `True` | Détecte si plusieurs instructions sont sur la même ligne. |
| Points-virgules | `True` | Identifie les utilisations de points-virgules. |

## <a name="text-group"></a>Groupe de texte

| Option | Valeur par défaut | Effet de linting |
| --- | --- | --- |
| Longueur limite de ligne | `False` | Définit si le linting marque les lignes plus longues que la valeur de l’option « Longueur maximale de ligne ». |
| Longueur maximale de ligne | 80 | Définit la longueur de ligne appliquée par l’option « Longueur limite de ligne ». |

## <a name="whitespace-group"></a>Groupe d’espaces blancs

Ces options, qui ont toutes la valeur `True` par défaut, contrôlent l’endroit où le linting identifie les problèmes d’espace blanc : utilisation de tabulations, utilisation de guillemets doubles, lignes vides de fin et espace blanc de fin.
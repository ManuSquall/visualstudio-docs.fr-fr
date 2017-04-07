---
title: "Mise en forme du code dans Python Tools pour Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: c1d7a19438b796c5666daecef33052e43d1f720f
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-python-code"></a>Mise en forme de code Python

La fonctionnalité de mise en forme du code dans Python Tools pour Visual Studio (PTVS) version 2.0 et les versions ultérieures vous permet de remettre rapidement en forme le code pour qu’il corresponde aux options de formatage préconfigurées.

- Pour mettre en forme une sélection : sélectionnez **Modifier > Avancé > Mettre la sélection en forme** ou appuyez sur Ctrl+E,F.
- Pour mettre en forme la totalité du fichier : sélectionnez **Modifier > Avancé > Mettre le document en forme** ou appuyez sur Ctrl+E,D.

Les options sont définies par le biais de la commande **Outils > Options > Éditeur de texte > Python > Mise en forme** et de ses sous-onglets, et correspondent par défaut à un sur-ensemble du [guide de style PEP 8](http://www.python.org/dev/peps/pep-0008/). L’onglet **Général** détermine les cas dans lesquels la mise en forme est appliquée ; les trois autres sous-onglets sont décrits dans les sections suivantes.

PTVS ajoute également la commande [Fill Comment Paragraph](#fill-comment-paragraph) (Redisposer le paragraphe de commentaires) au menu **Modifier > Avancé**, comme décrit ci-dessous.

## <a name="spacing"></a>Espacement

L’onglet **Espacement** contrôle l’emplacement d’insertion ou de suppression d’espaces autour des différentes constructions de langage. Chaque option possède trois valeurs possibles :

- Activé : garantit que l’espacement est appliqué.
- Désactivé : supprime tout espacement.
- Indéterminé : conserve la mise en forme d’origine.

Les tableaux ci-après fournissent des exemples des différentes options.

| Option des définitions de classe | Activé | Effacé |
| --- | --- | --- | 
| Insérer un espace entre le nom d’une déclaration de classe et une liste de bases | `class X (object): pass` | `class X(object): pass` | 
| Insérer un espace entre les parenthèses d’une liste de bases | `class X( object ): pass` | `class X(object): pass` |
| Insérer un espace entre les parenthèses d’une liste de bases vide | `class X( ): pass` | `class X(): pass` |

<br/>

| Option des définitions de fonction | Activé | Effacé |
| --- | --- | --- |
| Insérer un espace entre le nom d’une déclaration de fonction et une liste de paramètres | `def X (): pass` | `def X(): pass` | 
| Insérer un espace entre les parenthèses d’une liste de paramètres | `def X( a, b ): pass` | `def X(a, b): pass` |
| Insérer un espace entre les parenthèses d’une liste de paramètres vide | `def X( ): pass` | `def X(): pass` |
| Insérer des espaces autour du caractère « = » dans les valeurs de paramètre par défaut | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Insérer un espace avant et après les opérateurs d’annotation de renvoi | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Option des opérateurs | Activé | Effacé |
| --- | --- | --- |
| Insérer des espaces autour des opérateurs binaires | `a + b` | `a+b` |
| Insérer des espaces autour des attributions | `a = b` | `a=b` |

<br/>

| Option d’espacement d’expression | Activé | Effacé |
| --- | --- | --- |
| Insérer un espace entre le nom d’un appel de fonction et une liste d’arguments | `X ()` | `X()` |
| Insérer un espace dans les parenthèses de la liste d'arguments vide | `X( )` | `X()` |
| Insérer un espace dans les parenthèses de la liste d'arguments | `X( a, b )` | `X(a, b)` |
| Insérer un espace entre les parenthèses d’expression | `( a )` | `(a)` |
| Insérer un espace entre les parenthèses d’un tuple vide | `( )` | `()` |
| Insérer un espace entre les parenthèses d’un tuple | `( a, b )` | `(a, b)` |
| Insérer un espace dans des crochets vides | `[ ]` | `[]` |
| Insérer des espaces entre les crochets des listes | `[ a, b ]` | `[a, b]` |
| Insérer un espace avant un crochet ouvrant | `x [i]` | `x[i]` |
| Insérer un espace dans les crochets | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instructions

L’onglet **Instructions** contrôle la réécriture automatique de différentes instructions sous une forme plus proche du langage Python.

| Option | Avant la mise en forme | Après la mise en forme |
| --- | --- | --- |
| Placer les modules importés sur une nouvelle ligne | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Supprimer les points-virgules inutiles | `x = 42;` | `x = 42` |
| Placer plusieurs instructions sur une nouvelle ligne | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>Retour à la ligne

L’onglet **Retour à la ligne** vous permet de définir l’option **Maximum comment width** (Largeur maximale des commentaires) (définie par défaut sur la valeur 80). De cette façon, si l’option **Wrap comments that are too wide** (Renvoyer à la ligne les commentaires trop longs) est définie, PTVS mettra en forme les commentaires pour qu’ils ne dépassent pas cette largeur.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```



## <a name="fill-comment-paragraph-command"></a>Commande Fill Comment Paragraph (Redisposer le paragraphe de commentaires)

La commande **Modifier > Avancé > Fill Comment Paragraph (Redisposer le paragraphe de commentaires)** (Ctrl+E,Ctrl+P) redispose automatiquement et remet en forme le texte des commentaires en combinant les lignes courtes et en scindant les lignes longues.

Exemple :

```python
# foo 
# bar
# baz
```

devient :

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

devient :

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```

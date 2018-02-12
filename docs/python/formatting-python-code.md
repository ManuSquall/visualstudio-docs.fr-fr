---
title: Mise en forme du code Python dans Visual Studio | Microsoft Docs
description: "Guide pratique pour la remise en forme automatique de code Python dans Visual Studio, y compris l’espacement, les instructions, le retour à la ligne et les commentaires."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 5bab4c31662a4c376893e6f847a4f10eed3934dd
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="formatting-python-code"></a>Mise en forme de code Python

Dans Visual Studio, vous pouvez rapidement remettre en forme le code selon les options de mise en forme préconfigurées.

- Pour mettre en forme une sélection : sélectionnez **Modifier > Avancé > Mettre la sélection en forme** ou appuyez sur Ctrl+E,F.
- Pour mettre en forme la totalité du fichier : sélectionnez **Modifier > Avancé > Mettre le document en forme** ou appuyez sur Ctrl+E,D.

Les options sont définies par le biais de la commande **Outils > Options > Éditeur de texte > Python > Mise en forme** et de ses onglets imbriqués, et correspondent par défaut à un sur-ensemble du [guide de style PEP 8](http://www.python.org/dev/peps/pep-0008/). L’onglet **Général** détermine les cas dans lesquels la mise en forme est appliquée ; les paramètres des trois autres onglets sont décrits dans cette rubrique.

La [prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) ajoute également la commande [Remplir le paragraphe de commentaire](#fill-comment-paragraph-command) utile au menu **Modifier > Avancé**, comme décrit ci-dessous.

## <a name="spacing"></a>Espacement

L’onglet **Espacement** contrôle l’emplacement d’insertion ou de suppression d’espaces autour des différentes constructions de langage. Chaque option possède trois valeurs possibles :

- Activé : garantit que l’espacement est appliqué.
- Désactivé : supprime tout espacement.
- Indéterminé : conserve la mise en forme d’origine.

Les tableaux ci-après fournissent des exemples des différentes options :

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

Les options **Instructions** contrôlent la réécriture automatique de différentes instructions sous une forme plus proche du langage Python.

| Option | Avant la mise en forme | Après la mise en forme |
| --- | --- | --- |
| Placer les modules importés sur une nouvelle ligne | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Supprimer les points-virgules inutiles | `x = 42;` | `x = 42` |
| Placer plusieurs instructions sur une nouvelle ligne | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Retour à la ligne

L’onglet **Retour à la ligne** vous permet de définir l’option **Largeur maximale du commentaire** (la valeur par défaut est 80). Si l’option **Renvoyer à la ligne les commentaires trop longs** est définie, Visual Studio remet en forme les commentaires pour qu’ils ne dépassent pas cette largeur maximale.

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

La commande **Modifier > Avancé > Remplir le paragraphe de commentaire** (Ctrl+E, P) redispose et remet en forme le texte des commentaires en combinant les lignes courtes et en scindant les lignes longues.

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
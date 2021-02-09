---
title: Mettre en forme le code Python
description: Visual Studio peut reformater automatiquement du code Python, y compris les espacements, les instructions, le retour à la ligne et les commentaires.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7b03e99a70edd587c9dfe2a43d326a64d14b9193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887885"
---
# <a name="format-python-code"></a>Mettre en forme le code Python

Dans Visual Studio, vous pouvez rapidement remettre en forme le code selon les options de mise en forme préconfigurées.

- Pour mettre en forme une sélection : sélectionnez **modifier** la sélection du  >    >  **format** avancé ou appuyez sur **CTRL** + **E**  >  **F**.
- Pour mettre en forme l’ensemble du fichier : sélectionnez **modifier** le  >    >  **document au format** avancé ou appuyez sur **CTRL** + **E**  >  **D**.

Les options sont définies via **Outils**  >  **options**  >  **éditeur de texte**  >    >  **mise en forme** Python et leurs onglets imbriqués. Vous devez sélectionner **Afficher tous les paramètres** pour que ces options s’affichent :

![Options de mise en forme Python dans Visual Studio](media/options-editor-formatting.png)

Les options de mise en forme par défaut sont définies pour correspondre à un sur-ensemble du [guide de style PEP 8](https://www.python.org/dev/peps/pep-0008/). L’onglet **Général** détermine les cas dans lesquels la mise en forme est appliquée ; les paramètres des trois autres onglets sont décrits dans cet article.

La [prise en charge de Python dans Visual Studio](installing-python-support-in-visual-studio.md) ajoute également la commande [**Remplir le paragraphe de commentaire**](#fill-comment-paragraph-command) utile au menu **Modifier** > **Avancé**, comme dans une section ultérieure.

## <a name="spacing"></a>Espacement

L’onglet **Espacement** contrôle l’emplacement d’insertion ou de suppression d’espaces autour des différentes constructions de langage. Chaque option possède trois valeurs possibles :

- Activé : garantit que l’espacement est appliqué.
- Désactivé : supprime tout espacement.
- Indéterminé : conserve la mise en forme d’origine.

Les tableaux ci-après fournissent des exemples des différentes options :

| Option des définitions de classe | Activée | Désactivé |
| --- | --- | --- |
| **Insérer un espace entre le nom d’une déclaration de classe et une liste de bases** | `class X (object): pass` | `class X(object): pass` |
| **Insérer un espace entre les parenthèses d’une liste de bases** | `class X( object ): pass` | `class X(object): pass` |
| **Insérer un espace entre les parenthèses d’une liste de bases vide** | `class X( ): pass` | `class X(): pass` |

<br/>

| Option des définitions de fonction | Activée | Désactivé |
| --- | --- | --- |
| **Insérer un espace entre le nom d’une déclaration de fonction et une liste de paramètres** | `def X (): pass` | `def X(): pass` |
| **Insérer un espace entre les parenthèses d’une liste de paramètres** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **Insérer un espace entre les parenthèses d’une liste de paramètres vide** | `def X( ): pass` | `def X(): pass` |
| **Insérer des espaces autour du caractère « = » dans les valeurs de paramètre par défaut** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **Insérer un espace avant et après les opérateurs d’annotation de renvoi** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Option des opérateurs | Activée | Désactivé |
| --- | --- | --- |
| **Insérer des espaces autour des opérateurs binaires** | `a + b` | `a+b` |
| **Insérer des espaces autour des assignations** | `a = b` | `a=b` |

<br/>

| Option d’espacement d’expression | Activée | Désactivé |
| --- | --- | --- |
| **Insérer un espace entre le nom d’un appel de fonction et une liste d’arguments** | `X ()` | `X()` |
| **Insérer un espace dans les parenthèses de la liste d’arguments vide** | `X( )` | `X()` |
| **Insérer un espace dans les parenthèses de la liste d’arguments** | `X( a, b )` | `X(a, b)` |
| **Insérer un espace entre les parenthèses d’une expression** | `( a )` | `(a)` |
| **Insérer un espace entre les parenthèses d’un tuple vide** | `( )` | `()` |
| **Insérer un espace entre les parenthèses d’un tuple** | `( a, b )` | `(a, b)` |
| **Insérer un espace dans des crochets vides** | `[ ]` | `[]` |
| **Insérer des espaces entre les crochets des listes** | `[ a, b ]` | `[a, b]` |
| **Insérer un espace avant un crochet ouvrant** | `x [i]` | `x[i]` |
| **Insérer un espace dans les crochets** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instructions

Les options **Instructions** contrôlent la réécriture automatique de différentes instructions sous une forme plus proche du langage Python.

| Option | Avant la mise en forme | Après la mise en forme |
| --- | --- | --- |
| **Placer les modules importés sur une nouvelle ligne** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **Supprimer les points-virgules inutiles** | `x = 42;` | `x = 42` |
| **Placer chaque instruction d’un groupe de plusieurs instructions sur une nouvelle ligne** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>Renvoi à la ligne

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

**Modifier**  >  **Paramètres avancés**  >  **Remplir le paragraphe de commentaire** (**CTRL** + **E**  >  **P**) repasse et met en forme le texte de commentaire, en combinant les lignes courtes et en fractionnant les longueurs.

Par exemple :

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

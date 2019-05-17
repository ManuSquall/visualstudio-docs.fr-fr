---
title: 'Bien démarrer avec PTVS : Édition du code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550910"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Prise en main des outils Python pour Visual Studio : édition du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils Python pour Visual Studio offrent une expérience productive de l’éditeur Visual Studio pour Python.  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Commencez avec le modèle de projet d’application Python vide de base.  
  
 Commencez par taper une ligne `from … import` dans l'éditeur.  Vous voyez que la liste de saisie semi-automatique contextuelle contient une liste complète des modules qui sont disponibles pour l'importation.  Cette liste varie en fonction de votre version de Python et des bibliothèques que vous avez installées.  Utilisez la bibliothèque mathématique (math) comme exemple.  Remarquez que quand vous tapez, la liste de saisie semi-automatique filtre les éléments qui contiennent les caractères que vous avez tapés.  Complétez l'instruction en important l'identificateur `sin`.  
  
```python  
from math import sin  
  
```  
  
 Lors du codage, si vous utilisez un identificateur qui n'est pas lié, mais qui se trouve dans vos bibliothèques, les outils Python pour Visual Studio offrent une correction rapide contextuelle pour ajouter l'instruction d'importation dont vous avez besoin.  Par exemple, si vous avez tapé `cos`, **import from match** vous est proposé.  
  
 Vous pouvez utiliser un extrait de code pour générer du code.  Dans le menu Edition, cliquez sur IntelliSense, puis sur Insérer un extrait.  Choisissez maintenant Python, puis def.  Appelez la fonction `make_dot_string` et ajoutez un paramètre `x`.  Vous pouvez maintenant ajouter des assertions dans le fichier pour le développement axé sur des tests : vous voyez que les outils Python pour Visual Studio peuvent déjà proposer la nouvelle fonction dans les listes de saisie semi-automatique.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Revenez maintenant à la nouvelle fonction et commencez à écrire le corps suivant :  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Vous voyez que les outils Python pour Visual Studio supposent que le paramètre est un entier, car ils ont analysé les emplacements des appels à cette fonction.   Vous devez également utiliser la correction rapide pour importer `radians`.  
  
 Utilisez un autre extrait de code pour créer un bloc main en tapant `main` tout en haut, en appelant l’interface utilisateur des étiquettes actives et en utilisant la touche tabulation pour choisir « main def ... »  Écrivez une boucle de base pour appeler `make_dot_string`.  Vous voyez que les outils Python pour Visual Studio savent que la fonction retourne une chaîne si vous cliquez sur le point et que vous consultez les saisies semi-automatiques proposées.  Ces informations de type seront présentées tout au long de votre programme. Ainsi, partout où vos valeurs se retrouvent, nous pouvons fournir des info-bulles et des saisies semi-automatiques qui vous aideront à mieux comprendre et à écrire votre code.  
  
 Ajoutez un appel à print. Votre fonction main doit être similaire à ceci :  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Si vous appuyez sur F5, le code s'exécute dans une fenêtre cmd.exe et vous voyez un point oscillant d'avant en arrière.  
  
 Vous pouvez obtenir des instructions en regardant cette très courte [vidéo youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation du wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Vidéos sur le démarrage et l’exploration de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

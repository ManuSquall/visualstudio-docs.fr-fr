---
title: "Prise en main des outils Python pour Visual Studio&#160;: &#233;dition du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
caps.handback.revision: 4
---
# Prise en main des outils Python pour Visual Studio&#160;: &#233;dition du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les outils Python pour Visual Studio offrent une expérience productive de l'éditeur Visual Studio pour Python.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Commencez avec le modèle de projet d'application Python vide de base.  
  
 Commencez par taper une ligne `from … import` dans l'éditeur.  Vous voyez que la liste de saisie semi\-automatique contextuelle contient une liste complète des modules qui sont disponibles pour l'importation.  Cette liste varie en fonction de votre version de Python et des bibliothèques que vous avez installées.  Utilisez la bibliothèque mathématique \(math\) comme exemple.  Remarquez que quand vous tapez, la liste de saisie semi\-automatique filtre les éléments qui contiennent les caractères que vous avez tapés.  Complétez l'instruction en important l'identificateur `sin`.  
  
```python  
from math import sin  
  
```  
  
 Lors du codage, si vous utilisez un identificateur qui n'est pas lié, mais qui se trouve dans vos bibliothèques, les outils Python pour Visual Studio offrent une correction rapide contextuelle pour ajouter l'instruction d'importation dont vous avez besoin.  Par exemple, si vous avez tapé `cos`, vous voyez que **import from math** est proposé.  
  
 Vous pouvez utiliser un extrait de code pour générer du code.  Dans le menu Edition, cliquez sur IntelliSense, puis sur Insérer un extrait.  Choisissez maintenant Python, puis def.  Appelez la fonction `make_dot_string` et ajoutez un paramètre `x`.  Vous pouvez maintenant ajouter des assertions dans le fichier pour le développement axé sur des tests : vous voyez que les outils Python pour Visual Studio peuvent déjà proposer la nouvelle fonction dans les listes de saisie semi\-automatique.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Revenez maintenant à la nouvelle fonction et commencez à écrire le corps suivant :  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Vous voyez que les outils Python pour Visual Studio supposent que le paramètre est un entier, car ils ont analysé les emplacements des appels à cette fonction.  Vous devez également utiliser la correction rapide pour importer `radians`.  
  
 Utilisez un autre extrait de code pour créer un bloc main en tapant `main` tout en haut, en appelant l'interface utilisateur des balises actives et en utilisant la touche tabulation pour choisir « main def ... »  Écrivez une boucle de base pour appeler `make_dot_string`.  Vous voyez que les outils Python pour Visual Studio savent que la fonction retourne une chaîne si vous cliquez sur le point et que vous consultez les saisies semi\-automatiques proposées.  Ces informations de type seront présentées tout au long de votre programme. Ainsi, partout où vos valeurs se retrouvent, nous pouvons fournir des info\-bulles et des saisies semi\-automatiques qui vous aideront à mieux comprendre et à écrire votre code.  
  
 Ajoutez un appel à print. Votre fonction main doit être similaire à ceci :  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Si vous appuyez sur F5, le code s'exécute dans une fenêtre cmd.exe et vous voyez un point oscillant d'avant en arrière.  
  
 Vous pouvez voir ces instructions dans une très courte [vidéo youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## Voir aussi  
 [Documentation Wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Vidéos de prise en main et de présentation approfondie de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
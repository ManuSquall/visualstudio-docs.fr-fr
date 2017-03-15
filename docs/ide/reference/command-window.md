---
title: "Commande, fen&#234;tre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.CommandWindow"
helpviewer_keywords: 
  - "Commande (mode de la fenêtre Commande)"
  - "Commande (fenêtre)"
  - "Commande (fenêtre de l'IDE)"
  - "IDE, Commande (fenêtre)"
  - "Marque (mode de la fenêtre Commande)"
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Commande, fen&#234;tre
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La fenêtre **Commande** est utilisée pour exécuter des commandes ou des alias directement dans l'environnement de développement intégré \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Vous pouvez exécuter à la fois les commandes de menu et les commandes qui n'apparaissent dans aucun menu.  Pour afficher la fenêtre **Commande**, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Fenêtre Commande**.  
  
## Affichage des valeurs de variables  
 Pour vérifier la valeur d'une variable `varA`, utilisez la [Imprimer, commande](../../ide/reference/print-command.md) :  
  
```  
>Debug.Print varA  
```  
  
 Le point d'interrogation \(?\) est un alias pour `Debug.Print`, et cette commande peut donc également s'écrire :  
  
```  
>? varA  
```  
  
 Les deux versions de cette commande retournent la valeur de la variable `varA`.  
  
## Entrée de commandes  
 Le symbole supérieur à \(`>`\) apparaît à gauche de la fenêtre Commande comme une invite pour les nouvelles lignes.  Utilisez les touches de direction HAUT et BAS pour faire défiler les commandes précédemment émises.  
  
|Tâche|Solution|Exemple|  
|-----------|--------------|-------------|  
|Évaluer une expression.|Faites précéder l'expression d'un point d'interrogation \(`?`\).|`? myvar`|  
|Basculer vers une fenêtre Exécution.|Entrez `immed` dans la fenêtre sans supérieur au signe \(\>\)|`immed`|  
|Revenir à la fenêtre Commande à partir d'une commande Exécution.|Entrez `cmd` dans la fenêtre.|`>cmd`|  
  
 Les raccourcis suivants vous aident à naviguer en mode Commande.  
  
|Action|Emplacement du curseur|Combinaison de touches|  
|------------|----------------------------|----------------------------|  
|Parcourir la liste des commandes précédemment entrées.|Ligne d'entrée|HAUT et BAS & sur CTRL\+BAS|  
|Faire défiler le contenu de la fenêtre vers le haut.|Contenu de la fenêtre Commande|CTRL\+HAUT|  
|Faire défiler le contenu de la fenêtre vers le bas.|Contenu de la fenêtre Commande|BAS ou CTRL\+BAS|  
  
> [!TIP]
>  Vous pouvez copier une commande antérieure, en partie ou en totalité, vers la ligne d'entrée : à cet effet, faites défiler le contenu de la fenêtre jusqu'à la commande voulue, mettez en surbrillance le texte à copier, puis appuyez sur ENTRÉE.  
  
## Mode Marque  
 Lorsque vous cliquez sur n'importe quelle ligne précédente dans la fenêtre **Commande**, vous passez automatiquement en mode Marque.  Cela vous permet de sélectionner, de modifier et de copier le texte de commandes précédentes comme vous le feriez dans n'importe quel éditeur de texte, et de les coller dans la ligne active.  
  
## Le signe égal \(\=\)  
 La fenêtre utilisée pour entrer la commande `EvaluateStatement` détermine si un signe égal \(\=\) est interprété comme un opérateur de comparaison ou comme un opérateur d'assignation.  
  
 Dans la fenêtre de **Commande**, un signe égal \(\=\) est interprété comme un opérateur de comparaison.  Vous ne pouvez pas utiliser d'opérateurs d'assignation dans la fenêtre **Commande**.  Ainsi, si les valeurs des variables `varA` et `varB` sont différentes, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 retournera la valeur `False`.  
  
 Dans la fenêtre **Exécution**, par contraste, un signe égal \(\=\) est interprété comme un opérateur d'assignation.  Ainsi, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assignera à la variable `varA` la valeur de la variable `varB`.  
  
## Paramètres, commutateurs et valeurs  
 Certaines commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ont des arguments, des commutateurs et des valeurs obligatoires ou facultatifs.  L'utilisation de ces commandes est régie par un ensemble de règles spécifiques.  La commande complexe suivante est un exemple de commande destiné à clarifier la terminologie employée.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 Dans cet exemple :  
  
-   `Edit.ReplaceInFiles` est la commande  
  
-   `/case` et `/pattern:regex` sont des commutateurs \(précédés de la barre oblique \[\/\]\)  
  
-   `regex` est la valeur du commutateur `/pattern` ; le commutateur `/case` n'a pas de valeur  
  
-   `var[1-3]+` et `oldpar` sont des paramètres  
  
    > [!NOTE]
    >  Les commandes, paramètres, commutateurs ou valeurs qui comportent des espaces doivent être entourés de guillemets doubles \(""\).  
  
 En règle générale, les commutateurs et les paramètres peuvent être placés à n'importe quel endroit de la ligne de commande, à l'exception de la commande [Shell](../../ide/reference/shell-command.md), dont les commutateurs et les paramètres doivent respecter un ordre précis.  
  
 Pratiquement tous les commutateurs pris en charge par une commande peuvent avoir deux formes : une abrégée \(un seul caractère\) et une longue.  Plusieurs commutateurs de forme abrégée peuvent être regroupés.  Par exemple, `/p /g /m` peut aussi être spécifié sous la forme `/pgm`.  
  
 Lorsqu'une valeur est attribuée à un groupe de commutateurs, cette valeur s'applique à chacun des commutateurs.  Par exemple, `/pgm:123` équivaut à `/p:123 /g:123 /m:123`.  Si l'un des commutateurs du groupe n'accepte pas la valeur spécifiée, une erreur se produit.  
  
## Caractères d'échappement  
 La présence d'un signe d'insertion \(^\) dans une ligne de commande signifie que le caractère situé juste après ce signe est interprété littéralement, et non comme un caractère de contrôle.  Cela permet d'incorporer des guillemets \("\), des espaces, des barres obliques de début, des signes d'insertion ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur \(mais pas dans les noms de commutateurs\).  Par exemple :  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Un signe d'insertion a la même fonction qu'il soit ou non placé entre guillemets.  Si le signe d'insertion est le dernier caractère de la ligne de commande, il est ignoré.  L'exemple illustré ici montre comment rechercher le modèle « ^t ».  
  
## Utilisez des guillemets si des noms de tracé avec les espaces  
 Si, par exemple, vous souhaitez ouvrir un fichier qui possède un tracé contenant des espaces, vous devez placer des guillemets autour du tracé ou du segment de tracé contenant des espaces : C:\\ " fichiers programme » ou « fichiers C:\\Program ».  
  
## Voir aussi  
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
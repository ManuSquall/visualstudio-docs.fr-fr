---
title: "Fen&#234;tre Ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ImmediateWindow"
helpviewer_keywords: 
  - "évaluation de l'expression au moment du design"
  - "Exécution (fenêtre)"
  - "notifications d'exceptions de première chance"
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Fen&#234;tre Ex&#233;cution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La fenêtre **Exécution** est utilisée pour déboguer et évaluer les expressions, exécuter les instructions, imprimer les valeurs des variables, etc.  Ce mode vous permet d'entrer des expressions qui doivent être évaluées ou exécutées par le langage de développement lors du processus de débogage.  Pour afficher la fenêtre **Exécution**, ouvrez un projet à modifier, puis choisissez **Windows** dans le menu **Déboguer** et sélectionnez **Exécution**, ou appuyez sur CTRL\+ALT\+I.  
  
 Vous pouvez utiliser cette fenêtre pour émettre des commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individuelles.  Parmi les commandes disponibles, `EvaluateStatement` peut être utilisée pour assigner des valeurs aux variables.  Désormais, la fenêtre **Exécution** prend également en charge Intellisense.  
  
## Affichage des valeurs de variables  
 Cette fenêtre peut être particulièrement utile pendant le débogage d'une application.  Par exemple, pour vérifier la valeur d'une variable `varA`, vous pouvez utiliser la commande Imprimer \([Imprimer, commande](../../ide/reference/print-command.md)\) :  
  
```  
>Debug.Print varA  
```  
  
 Le point d'interrogation \(?\) est un alias pour `Debug.Print`, et cette commande peut donc également s'écrire :  
  
```  
>? varA  
```  
  
 Les deux versions de cette commande retournent la valeur de la variable `varA`.  
  
> [!NOTE]
>  Pour émettre une commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la fenêtre **Exécution**, vous devez faire précéder la commande d'un signe supérieur à \(\>\).  Pour entrer plusieurs commandes, basculez vers le mode **Commande**.  
  
## Évaluation des expressions au moment du design  
 Vous pouvez utiliser la fenêtre **Immédiat** pour exécuter une fonction ou une sous\-routine au moment du design.  
  
#### Pour afficher une fonction au moment du design  
  
1.  Copiez le code suivant dans une application console [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] :  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Immédiat**.  
  
3.  Tapez `?MyFunction(2)` dans la fenêtre **Immédiat** et appuyez sur Entrée.  
  
     La fenêtre **Immédiat** exécute `MyFunction` et affiche `4`.  
  
 Si la fonction ou la sous\-routine contient un point d'arrêt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arrête l'exécution à ce point.  Vous pouvez utiliser ensuite les fenêtres du débogueur pour examiner l'état de votre programme.  Pour plus d'informations, consultez [Procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 Vous ne pouvez pas utiliser l'évaluation d'expression au moment du design dans les types de projets qui requièrent le démarrage d'un environnement d'exécution \(projets [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)], projets Web, projets Smart Device et projets SQL\).  
  
### Évaluation des expressions au moment du design dans les solutions à projets multiples  
 Lors de l'établissement du contexte pour l'évaluation d'expression au moment du design, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fait référence au projet actuellement sélectionné dans l'Explorateur de solutions.  Si aucun projet n'est sélectionné dans l'Explorateur de solutions, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tente alors d'évaluer la fonction par rapport au projet de démarrage.  Si la fonction ne peut pas être évaluée dans le contexte actuel, un message d'erreur s'affiche.  Si vous essayez d'évaluer une fonction dans un projet qui n'est pas le projet de démarrage pour la solution et que vous recevez une erreur, essayez de sélectionner le projet dans l'Explorateur de solutions et tentez à nouveau l'évaluation.  
  
## Entrée de commandes  
 Vous devez entrer le signe supérieur à \(\>\) lorsque vous émettez des commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la fenêtre **Exécution** .  Utilisez les touches de direction HAUT et BAS pour faire défiler les commandes précédemment émises.  
  
|Tâche|Solution|Exemple|  
|-----------|--------------|-------------|  
|Évaluer une expression.|Faites précéder l'expression d'un point d'interrogation \(?\).|`? a+b`|  
|En mode Exécution, passer temporairement en mode Commande \(pour exécuter une seule commande\).|Entrez la commande en la faisant précéder du signe supérieur à \(\>\).|`>alias`|  
|Basculez vers la fenêtre Commande.|Entrez `cmd` dans la fenêtre, en le faisant précéder d'un signe supérieur à \(\>\).|`>cmd`|  
|Revenez à la fenêtre Exécution.|Entrez `immed` dans la fenêtre sans le signe supérieur à \(\>\).|`immed`|  
  
## Mode Marque  
 Lorsque vous cliquez sur n'importe quelle ligne précédente dans la fenêtre **Exécution**, vous passez automatiquement en mode Marque.  Cela vous permet de sélectionner, de modifier et de copier le texte de commandes précédentes comme vous le feriez dans n'importe quel éditeur de texte, et de les coller dans la ligne active.  
  
## Le signe égal \(\=\)  
 La fenêtre utilisée pour entrer la commande `EvaluateStatement` détermine si un signe égal \(\=\) est interprété comme un opérateur de comparaison ou comme un opérateur d'assignation.  
  
 Dans la fenêtre **Exécution**, un signe égal \(\=\) est interprété comme un opérateur d'assignation.  Ainsi, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assignera à la variable `varA` la valeur de la variable `varB`.  
  
 En revanche, dans la fenêtre de **Commande**, un signe égal \(\=\) est interprété comme un opérateur de comparaison.  Vous ne pouvez pas utiliser d'opérations d'assignation dans la fenêtre **Commande**.  Ainsi, si les valeurs des variables `varA` et `varB` sont différentes, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 retournera la valeur `False`.  
  
## Notifications des exceptions de première chance  
 Dans certaines configurations de paramètres, les notifications d'exception de première chance sont affichées dans la fenêtre **Immédiat**.  
  
#### Pour basculer les notifications d'exceptions de première chance dans la fenêtre Immédiat  
  
1.  Dans le menu **Affichage**, cliquez sur **Autres fenêtres** , puis sur **Sortie**.  
  
2.  Cliquez avec le bouton droit sur la zone de texte de la fenêtre **Sortie** et sélectionnez ou désélectionnez **Messages d'exception**.  
  
## Voir aussi  
 [Naviguer dans le code avec le débogueur](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Débogage dans Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Principes de base du débogueur](../../debugger/debugger-basics.md)   
 [Procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Utilisation d'expressions régulières dans Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
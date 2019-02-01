---
title: Utilisation d’IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb859fe5e66dbfcc1f43dfff3c0744c84066054b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758826"
---
# <a name="using-intellisense"></a>Using IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense est le terme général qui désigne un certain nombre de fonctionnalités : Liste des membres, Informations sur les paramètres, Info express et Compléter le mot. Ces fonctionnalités vous aident à en savoir plus sur le code que vous utilisez, à assurer le suivi des paramètres que vous tapez et à ajouter des appels aux propriétés et aux méthodes en quelques séquences de touches.  
  
 De nombreux aspects d'IntelliSense sont spécifiques au langage. Pour plus d'informations sur IntelliSense pour différents langages, consultez les rubriques répertoriées sous Voir aussi.  
  
## <a name="list-members"></a>Liste des membres  
 Une liste de membres valides d'un type (ou d'un espace de noms) apparaît lorsque vous tapez un caractère déclencheur (par exemple, un point (`.`) en code managé ou `::` en C++). Si vous continuez d'entrer des caractères, la liste est filtrée pour inclure uniquement les membres qui commencent par ces caractères.  
  
 Après avoir sélectionné un élément, insérez-le dans votre code en appuyant sur la touche Tab ou en tapant un espace. Si vous sélectionnez un élément et que vous tapez un point, l'élément apparaît suivi du point, ce qui provoque l'affichage d'une autre liste de membres. Lorsque vous sélectionnez un élément, mais avant de l'insérer, vous obtenez des informations express le concernant.  
  
 Dans la liste des membres, l'icône de gauche représente le type de membre, tel que l'espace de noms, la classe, la fonction ou la variable. Pour obtenir une liste des icônes, consultez [Icônes de l’Explorateur d’objets et de la fenêtre Affichage de classes](../ide/class-view-and-object-browser-icons.md). La liste pouvant être relativement longue, vous pouvez appuyer sur PG.PRÉC et PG.SUIV pour vous déplacer vers le haut ou vers le bas dans la liste.  
  
 ![Liste des membres Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")  
  
 Vous pouvez appeler la fonctionnalité **Liste des membres** manuellement en appuyant sur Ctrl+J, en cliquant sur **Modifier/IntelliSense/Liste des membres** ou en cliquant sur le bouton **Liste des membres** dans la barre d’outils de l’éditeur. Lorsque la liste des membres est appelée sur une ligne vide ou en dehors d'une portée reconnue, elle affiche des symboles dans l'espace de noms global.  
  
 Pour désactiver par défaut la liste des membres (afin qu’elle n’apparaisse pas sauf si elle est explicitement appelée), accédez à **Outils/Options/Tous les langages** et désélectionnez **Répertorier automatiquement les membres**. Si vous souhaitez désactiver la liste des membres uniquement pour un langage spécifique, accédez à la page de paramètres **Général** pour ce langage.  
  
 Vous pouvez également passer en mode suggestion, où seul le texte que vous tapez est inséré dans le code. Par exemple, si vous entrez un identificateur qui ne figure pas dans la liste et que vous appuyez sur Tab, en mode de saisie semi-automatique l'entrée remplace l'identificateur typé. Pour basculer entre le mode saisie semi-automatique et le mode suggestion, appuyez sur Ctrl+Alt+Espace ou cliquez sur **Modifier/IntelliSense/Activer-Désactiver le mode de saisie semi-automatique**.  
  
## <a name="parameter-info"></a>Informations sur les paramètres  
 Informations sur les paramètres fournit des informations sur le nombre, les noms et les types des paramètres requis par une méthode, un paramètre de type générique d’attribut (en C#) ou un modèle (en C++).  
  
 Le paramètre suivant à taper pour la fonction vous est indiqué en gras. Pour les fonctions surchargées, vous pouvez utiliser les touches de direction Haut et Bas pour consulter les différentes informations de paramètres concernant les surcharges de fonction.  
  
 ![Informations sur les paramètres](../ide/media/vs2015-param-info.png "VS2015_param_Info")  
  
 Lorsque vous annotez des fonctions et des paramètres avec les commentaires de documentation XML, les commentaires apparaissent comme Informations sur les paramètres. Pour plus d’informations, consultez [Insertion de commentaires dans le code XML](../ide/supplying-xml-code-comments.md).  
  
 Vous pouvez appeler manuellement la fonctionnalité Informations sur les paramètres en cliquant sur **Edition/IntelliSense/Informations sur les paramètres**, en appuyant sur Ctrl+Maj+Espace ou en cliquant sur le bouton **Informations sur les paramètres** dans la barre d’outils de l’éditeur.  
  
## <a name="quick-info"></a>Info express  
 Infos express affiche la déclaration complète de tout identificateur dans votre code.  
  
 ![Info express dans Visual Studio](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")  
  
 Quand vous sélectionnez un membre dans la zone **Liste des membres**, l’info-bulle Info express s’affiche aussi.  
  
 ![Informations sur les paramètres dans un fichier de code C&#35;](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")  
  
 Vous pouvez appeler manuellement la fonctionnalité Info express en cliquant sur **Edition/IntelliSense/Info express**, en appuyant sur Ctrl+I ou en cliquant sur le bouton **Info express** dans la barre d’outils de l’éditeur.  
  
 Si une fonction est surchargée, il est possible que la fonctionnalité IntelliSense n'affiche pas les informations de toutes les formes de la surcharge.  
  
 Vous pouvez désactiver la fonctionnalité Info express dans C++ en définissant **Outils/Options/Éditeur de texte/C/C++/Avancé/Info express automatique** sur `false`.  
  
## <a name="complete-word"></a>Compléter le mot  
 L'option Compléter le mot entre automatiquement la fin d'un nom de variable, de commande ou de fonction une fois que vous avez entré assez de caractères pour qu'il ne subsiste plus aucune ambiguïté. Vous pouvez appeler la fonctionnalité Compléter le mot en cliquant sur **Edition/IntelliSense/Compléter le mot**, en appuyant sur Ctrl+Espace ou en cliquant sur le bouton **Compléter le mot** dans la barre d’outils de l’éditeur.  
  
## <a name="intellisense-options"></a>Options IntelliSense  
 Les options IntelliSense sont activées par défaut. Pour les désactiver, cliquez sur **Outils/Options/Éditeur de texte** et désélectionnez **Informations sur les paramètres** ou **Répertorier automatiquement les membres** si vous n’avez pas besoin de la fonctionnalité Liste des membres.  
  
## <a name="troubleshooting-intellisense"></a>Résolution des problèmes liés à IntelliSense  
 Dans certains cas, les options IntelliSense ne fonctionneront peut-être pas comme vous l'attendez.  
  
 **Le curseur se trouve en dessous d’une erreur de code.** Vous ne pourrez peut-être pas utiliser IntelliSense si une fonction incomplète ou une autre erreur existe dans le code situé au-dessus du curseur, car IntelliSense ne pourra peut-être pas analyser les éléments du code. Vous pouvez résoudre ce problème en commentant le code applicable.  
  
 **Le curseur se trouve dans un commentaire de code.** Vous ne pouvez pas utiliser IntelliSense si le curseur se trouve dans un commentaire de votre fichier source.  
  
 **Le curseur se trouve dans un littéral de chaîne.** Vous ne pouvez pas utiliser IntelliSense si le curseur se trouve entre les guillemets entourant un littéral de chaîne, comme dans l'exemple suivant :  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Les options automatiques sont désactivées.** Par défaut, IntelliSense est automatiquement utilisé, mais vous pouvez le désactiver. Même lorsque la saisie semi-automatique des instructions est désactivée, vous pouvez appeler une fonctionnalité IntelliSense.  
  
## <a name="see-also"></a>Voir aussi  
 [Options IntelliSense spécifiques à Visual Basic](../ide/visual-basic-specific-intellisense.md)   
 [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md)   
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Insertion de commentaires dans le code XML](../ide/supplying-xml-code-comments.md)

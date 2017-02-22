---
title: "&#201;tape&#160;2&#160;: ajouter un objet al&#233;atoire et une liste d&#39;ic&#244;nes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &#201;tape&#160;2&#160;: ajouter un objet al&#233;atoire et une liste d&#39;ic&#244;nes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette étape, vous créez un ensemble de symboles correspondants pour le jeu.  Chaque symbole est ajouté à deux cellules aléatoires dans le TableLayoutPanel du formulaire.  Pour cela, vous devez utiliser deux instructions `new` pour créer deux objets.  Le premier est un objet `Random` identique à celui que vous avez utilisé dans le jeu du quiz mathématique.  Il est utilisé dans ce code pour choisir de façon aléatoire des cellules dans le TableLayoutPanel.  Le second objet, qui est peut\-être nouveau pour vous, est un objet `List` qui sert à stocker les symboles choisis au hasard.  
  
### Pour ajouter un objet aléatoire et une liste d'icônes  
  
1.  Dans l'**Explorateur de solutions**, choisissez **Form1.cs** si vous utilisez Visual C\#, ou **Form1.vb** si vous utilisez Visual Basic, puis, dans la barre de menus, choisissez **Affichage**, **Code**.  Comme alternative, vous pouvez appuyer sur **F7** ou double\-cliquer sur **Form1** dans l'**Explorateur de solutions**.  
  
     Cela affiche le module de code derrière Form1.  
  
2.  Dans le code existant, ajoutez le code suivant :  
  
     [!code-cs[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]  
  
     Si vous utilisez Visual C\#, veillez à placer le code après l'accolade ouvrante et juste après la déclaration de classe \(`public partial class Form1 : Form`\).  Si vous utilisez Visual Basic, placez le code juste après la déclaration de classe \(`Public Class Form1`\).  
  
3.  Lorsque vous ajoutez l'objet `List`, notez la fenêtre **IntelliSense** qui s'ouvre.  L'exemple ci\-dessous est en Visual C\#, mais un texte similaire s'affiche lorsque vous ajoutez une liste en Visual Basic.  
  
     ![Fenêtre Propriétés affichant l'événement Click](../ide/media/express_listintellisense.png "Express\_ListIntellisense")  
Fenêtre IntelliSense  
  
    > [!NOTE]
    >  La fenêtre IntelliSense apparaît uniquement lorsque vous entrez du code manuellement.  Si vous effectuez un copier\-coller du code, elle n'apparaît pas.  
  
     Si vous examinez le code \(et les remarques\) par petites sections, vous le comprendrez plus facilement.  Vos programmes peuvent utiliser des objets `List` pour effectuer le suivi de nombreux types d'éléments différents.  Une liste peut contenir des nombres, des valeurs True\/False, du texte ou d'autres objets.  Un objet `List` peut même contenir d'autres objets `List`.  Une liste est composée d'*éléments* et chacune d'elles ne contient qu'un seul type d'éléments.  Ainsi, une liste de nombres ne peut contenir que des nombres et vous ne pouvez pas y ajouter de texte.  De même, vous ne pouvez pas ajouter de nombres dans une liste de valeurs true\/false.  
  
     Lorsque vous créez un objet `List` à l'aide d'une instruction `new`, vous devez spécifier le type de données que vous souhaitez y stocker.  C'est la raison pour laquelle l'info\-bulle en haut de la fenêtre **IntelliSense** affiche les types d'éléments dans la liste.  C'est également ce que signifient `List<string>` \(en Visual C\#\) et `List(Of String)` \(en Visual Basic\) : ils correspondent à un objet `List` qui contient des éléments de type `string`.  Une chaîne est utilisée par votre programme pour stocker du texte, comme indiqué par l'info\-bulle à droite de la fenêtre **IntelliSense**.  
  
4.  Pourquoi un tableau temporaire doit\-il d'abord être créé en Visual Basic, alors que la liste peut être créée avec une seule instruction en Visual C\# ?  Cela est dû au fait que le langage Visual C\# a des *initialiseurs de collection* qui préparent la liste à accepter des valeurs.  En Visual Basic, vous pouvez utiliser un initialiseur de collection.  Toutefois, nous vous recommandons d'utiliser le code précédent pour des raisons de compatibilité avec la version antérieure de Visual Basic.  
  
     Lorsque vous utilisez un initialiseur de collection avec une instruction `new`, une fois que le nouvel objet `List` a été créé, le programme le remplit avec les données que vous avez fournies entre les accolades.  Dans ce cas, vous obtenez une liste de chaînes nommées **icônes**, et cette liste sera initialisée de sorte à contenir seize chaînes.  Chacune de ces chaînes est une lettre unique, et elles correspondent toutes aux icônes qui seront dans les contrôles Label.  Ainsi, le jeu comportera une paire de points d'exclamation, une paire de lettres N majuscules, une paire de virgules, etc. \(Lorsque la police Webdings est affectée à ces caractères, ils apparaissent sous la forme de symboles, tels qu'un bus, un vélo, une araignée, etc.\) En tout, votre objet `List` contiendra seize chaînes, une pour chaque cellule du volet TableLayoutPanel.  
  
    > [!NOTE]
    >  Dans Visual Basic, vous obtenez le même résultat, mais les chaînes sont d'abord insérées dans un tableau temporaire, qui est ensuite converti en objet `List`.  Un tableau est semblable à une liste, sauf que les tableaux sont créés avec une taille fixe, par exemple.  Les listes peuvent se réduire et s'agrandir autant que nécessaire, ce qui est important dans ce programme.  
  
### Pour continuer ou examiner  
  
-   Pour passer à l'étape suivante du didacticiel, consultez [Étape 3 : assigner une icône aléatoire à chaque contrôle Label](../Topic/Step%203:%20Assign%20a%20Random%20Icon%20to%20Each%20Label.md).  
  
-   Pour revenir à l'étape précédente du didacticiel, consultez [Étape 1 : créer un projet et ajouter une table au formulaire](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
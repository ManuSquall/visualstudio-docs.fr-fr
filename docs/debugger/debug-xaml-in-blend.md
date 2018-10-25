---
title: Déboguer XAML dans Blend | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f2fa98a1e737ca06cc9b190da349b6e735dcb7df
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838957"
---
# <a name="debug-xaml-in-blend"></a>Déboguer XAML dans Blend
Vous pouvez utiliser les outils de [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] pour déboguer le code XAML dans votre application. Lorsque vous générez un projet, toutes les erreurs sont affichées dans le **résultats** Panneau de configuration. Double-cliquez sur une erreur pour localiser le balisage associé à l'erreur. Si vous avez besoin de plus d’espace de travail, vous pouvez masquer la **résultats** panneau en appuyant sur F12.  

## <a name="syntax-errors"></a>Erreurs de syntaxe  
 Des erreurs de syntaxe se produisent si votre code XAML, ou les fichiers code-behind ne suivent pas les règles de mise en forme du langage. La description de l’erreur peut vous aider à la résoudre. La liste spécifie également le nom du fichier et le numéro de ligne où l’erreur se produit. Les erreurs XAML sont répertoriés sur le **balisage** onglet dans le **résultats** Panneau de configuration.  

> [!TIP]
>  XAML est un langage de balisage basé sur XML qui suit les règles de syntaxe de XML.  

 Certaines causes courantes d’erreurs de syntaxe XAML se présentent comme suit :  

- Un mot clé n’a pas été correctement orthographié ou la casse est erronée.  

- Des guillemets sont manquants autour d'attributs ou de chaînes de texte.  

- Il manque une étiquette de fermeture à un élément XAML.  

- Il existe un élément XAML à un emplacement non autorisé.  

  Pour plus d’informations sur la syntaxe XAML courante, consultez [guide de la syntaxe XAML de base](http://go.microsoft.com/fwlink/?LinkId=329942).  

  Vous pouvez également identifier et résoudre des erreurs de syntaxe code-behind simples, des erreurs de compilation et des erreurs d'exécution dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Toutefois, il peut être plus facile d'identifier et de résoudre les erreurs code-behind dans Visual Studio.  

### <a name="debugging-sample-xaml-code"></a>Débogage d'un exemple de code XAML  
 L'exemple suivant détaille toutes les étapes d'une session de débogage de code XAML simple dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

##### <a name="to-create-a-project"></a>Pour créer un projet  

1. Dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], ouvrez le **fichier** menu, puis sur **nouveau projet**.  

    Dans le **nouveau projet** boîte de dialogue, une liste des types de projets apparaît sur le côté gauche. Lorsque vous cliquez sur un type de projet, les modèles de projet associés à ce type apparaissent sur le côté droit.  

2. Dans la liste des types de projets, cliquez sur **Windows universel**.  

3. Dans la liste des modèles de projet, cliquez sur **application vide (Windows universel)**.  

4. Dans le **nom** zone de texte, tapez `DebuggingSample`.  

5. Dans le **emplacement** texte, vérifiez l’emplacement du projet.  

6. Dans le **langage** , cliquez sur **Visual C#**, puis cliquez sur **OK** pour créer le projet.  

7. Avec le bouton droit sur l’aire de conception, puis cliquez sur **afficher la Source** pour basculer vers **fractionnement** vue.  

8. Copiez le code suivant en cliquant sur le **copie** lien dans le coin supérieur droit du code.  

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
   ```  

9. Recherchez la valeur par défaut **grille**et collez le code entre les balises **grille** balises. Lorsque vous avez terminé, votre code doit ressembler au code suivant :  

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
    ```  

10. Appuyez sur Ctrl+Maj+B pour générer le projet.  

    Un message d’erreur s’affiche vous indiquant que le projet ne peut pas être généré, et le **résultats** panneau répertoriant les erreurs apparaît au bas de l’application.  

    ![Déboguer XAML dans Blend pour Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")  

### <a name="resolving-xaml-errors"></a>Résolution d'erreurs XAML  
 Quand des erreurs XAML sont détectées, l'aire de conception affiche une alerte indiquant que votre projet contient un balisage non valide. Comme vous résolvez les erreurs, la liste d’erreurs dans le **résultats** panneau est mis à jour. Quand vous avez résolu toutes les erreurs, l'aire de conception est activée et votre application y est affichée.  

##### <a name="to-resolve-the-xaml-errors"></a>Pour résoudre les erreurs XAML  

1. Double-cliquez sur la première erreur de la liste. La description est : « La valeur '<' n'est pas valide dans un attribut ». Lorsque vous double-cliquez sur l'erreur, le pointeur trouve l'emplacement correspondant dans le code. Le `<` est valide, étant placé devant `Button` et non pas devant un attribut, comme indiqué dans le message d'erreur. Si vous examinez la ligne de code précédente, vous remarquez que le guillemet anglais fermant de l'attribut `Top` est manquant. Tapez le guillemet anglais fermant. Notez que la liste d’erreurs dans le **résultats** panneau mises à jour pour refléter vos modifications.  

2. Double-cliquez sur la description « '0' n’est pas valide au début d’un nom. » `Margin="0,149,0,0"` semble être correct. Toutefois, notez que le codage en couleur de `Margin` n'est pas le même que celui des autres instances de `Margin` dans le code. L'absence de guillemets anglais fermants dans la paire nom/valeur précédente (`VerticalAlignment="Top`) fait que `Margin="` est lu comme faisant partie de la valeur de l'attribut précédent, et 0 est lu comme le début de la paire nom/ valeur. Tapez le guillemet anglais fermant pour `Top`. La liste d’erreurs dans le **résultats** panneau mises à jour pour refléter vos modifications.  

3. Double-cliquez sur l’erreur restante : « Le Bouton d’étiquette XML de fermeture ne correspond pas » Le pointeur se trouve à la fermeture **grille** balise (`</Grid>`), suggérant que l’erreur se trouve dans le `Grid` objet. Notez que l’étiquette de fermeture est manquante dans le deuxième objet `Button`. Après avoir ajouté la fermeture `/`, le **résultats** liste du panneau est mis à jour. Ces erreurs initiales sont à présent résolues, mais deux erreurs supplémentaires ont été identifiées.  

4. Double-cliquez sur « Le membre "contenu" n'est pas reconnu ou n'est pas accessible. ». Le `c` dans `content` devrait être en majuscules. Remplacez le « c » minuscule par un « c » majuscule.  

5. Double-cliquez sur « la propriété « Mame » n’existe pas dans le '<http://schemas.microsoft.com/winfx/2006/xaml>' espace de noms. » Le « M » dans « Mame » devrait être un « N ». Remplacez le « M » par un « N ». Maintenant que le code XAML peut être analysé, l'application s'affiche sur l'aire de conception.  

    ![Débogage de XAML dans Blend pour Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")  

    Appuyez sur Ctrl+Maj+B pour générer votre projet et vous assurer qu’il ne contient plus aucune erreur.  

## <a name="debugging-in-visual-studio"></a>Débogage dans Visual Studio  
 Vous pouvez ouvrir les projets [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] dans Visual Studio afin de déboguer plus facilement le code dans votre application. Pour ouvrir un [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] de projet dans Visual Studio, cliquez sur le projet dans le **projets** panneau, puis cliquez sur **modifier dans Visual Studio**. Une fois la session de débogage terminée dans Visual Studio, appuyez sur Ctrl+Maj+S pour enregistrer toutes vos modifications, puis revenez à [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Vous êtes alors invité à recharger le projet. Cliquez sur **Oui pour tout** pour continuer à travailler dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

 Pour plus d’informations sur le débogage de votre application, consultez [UWP de déboguer des applications dans Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  

## <a name="getting-help"></a>Obtenir de l’aide  
 Si vous avez besoin d’aide plus débogage votre [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] application, vous pouvez rechercher le [forums des Communautés application UWP](http://go.microsoft.com/fwlink/?LinkId=280308) pour les publications relatives à votre problème ou poser une question.

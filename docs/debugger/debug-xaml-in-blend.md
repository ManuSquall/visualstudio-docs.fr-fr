---
title: Déboguer XAML dans Blend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: c7efe1fc6b4a1bf47a2b9d2fe34eee203fcf014a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018925"
---
# <a name="debug-xaml-in-blend"></a>Déboguer XAML dans Blend
Vous pouvez utiliser les outils de [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] pour déboguer le code XAML dans votre application. Lors de la création d’un projet, toutes les erreurs sont affichées dans le volet **Résultats**. Double-cliquez sur une erreur pour localiser le balisage associé à l'erreur. Si votre travail nécessite davantage d’espace, appuyez sur F12 pour masquer le volet **Résultats**.  

## <a name="syntax-errors"></a>Erreurs de syntaxe  
 Des erreurs de syntaxe se produisent si votre code XAML, ou les fichiers code-behind ne suivent pas les règles de mise en forme du langage. La description de l’erreur peut vous aider à la résoudre. La liste spécifie également le nom du fichier et le numéro de ligne où l’erreur se produit. Les erreurs XAML sont répertoriées dans l’onglet **Balisage** du volet **Résultats**.  

> [!TIP]
>  XAML est un langage de balisage basé sur XML qui suit les règles de syntaxe de XML.  

 Certaines causes courantes d’erreurs de syntaxe XAML se présentent comme suit :  

- Un mot clé n’a pas été correctement orthographié ou la casse est erronée.  

- Des guillemets sont manquants autour d'attributs ou de chaînes de texte.  

- Il manque une étiquette de fermeture à un élément XAML.  

- Il existe un élément XAML à un emplacement non autorisé.  

  Pour plus d’informations sur la syntaxe XAML de base, consultez la page [Guide de base de la syntaxe XAML](http://go.microsoft.com/fwlink/?LinkId=329942).  

  Vous pouvez également identifier et résoudre des erreurs de syntaxe code-behind simples, des erreurs de compilation et des erreurs d'exécution dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Toutefois, il peut être plus facile d'identifier et de résoudre les erreurs code-behind dans Visual Studio.  

### <a name="debugging-sample-xaml-code"></a>Débogage d'un exemple de code XAML  
 L'exemple suivant détaille toutes les étapes d'une session de débogage de code XAML simple dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

##### <a name="to-create-a-project"></a>Pour créer un projet  

1. Dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], ouvrez le menu **Fichier**, puis cliquez sur **Nouveau projet**.  

    Dans la boîte de dialogue **Nouveau projet**, une liste de types de projet apparaît sur le côté gauche. Lorsque vous cliquez sur un type de projet, les modèles de projet associés à ce type apparaissent sur le côté droit.  

2. Dans la liste des types de projets, cliquez sur **Windows universel**.  

3. Dans la liste des modèles de projet, cliquez sur **application vide (Windows universel)**.  

4. Dans le **nom** zone de texte, tapez `DebuggingSample`.  

5. Dans la zone de texte **Emplacement**, vérifiez l’emplacement du projet.  

6. Dans la liste **Langage**, cliquez sur **Visual C#**, puis sur **OK** pour créer le projet.  

7. Cliquez avec le bouton droit sur l’aire de conception, puis cliquez sur **Afficher la source** pour passer à la vue **Fractionné**.  

8. Copiez le code suivant en cliquant sur le lien **Copier** en haut à droite du code.  

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
   ```  

9. Recherchez la **Grille** par défaut, et collez le code entre les balises **Grid** de début et de fin. Lorsque vous avez terminé, votre code doit ressembler au code suivant :  

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

    Un message d’erreur s’affiche vous indiquant que le projet ne peut pas être généré et le volet **Résultats** listant les erreurs apparaît au bas de l’application.  

    ![Déboguer XAML dans Blend pour Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")  

### <a name="resolving-xaml-errors"></a>Résolution d'erreurs XAML  
 Quand des erreurs XAML sont détectées, l'aire de conception affiche une alerte indiquant que votre projet contient un balisage non valide. Au fur et à mesure de la résolution des erreurs, la liste d’erreurs dans le volet **Résultats** est mise à jour. Quand vous avez résolu toutes les erreurs, l'aire de conception est activée et votre application y est affichée.  

##### <a name="to-resolve-the-xaml-errors"></a>Pour résoudre les erreurs XAML  

1. Double-cliquez sur la première erreur de la liste. La description est : « La valeur '<' n'est pas valide dans un attribut ». Lorsque vous double-cliquez sur l'erreur, le pointeur trouve l'emplacement correspondant dans le code. Le `<` est valide, étant placé devant `Button` et non pas devant un attribut, comme indiqué dans le message d'erreur. Si vous examinez la ligne de code précédente, vous remarquez que le guillemet anglais fermant de l'attribut `Top` est manquant. Tapez le guillemet anglais fermant. Notez que la liste d’erreurs dans le volet **Résultats** est mise à jour au fur et à mesure de vos modifications.  

2. Double-cliquez sur la description « '0' n’est pas valide au début d’un nom. » `Margin="0,149,0,0"` semble être correct. Toutefois, notez que le codage en couleur de `Margin` n'est pas le même que celui des autres instances de `Margin` dans le code. L'absence de guillemets anglais fermants dans la paire nom/valeur précédente (`VerticalAlignment="Top`) fait que `Margin="` est lu comme faisant partie de la valeur de l'attribut précédent, et 0 est lu comme le début de la paire nom/ valeur. Tapez le guillemet anglais fermant pour `Top`. La liste d’erreurs dans le volet **Résultats** est mise à jour au fur et à mesure de vos modifications.  

3. Double-cliquez sur l’erreur restante : « Le Bouton d’étiquette XML de fermeture ne correspond pas » Le pointeur se trouve sur la balise **Grid** de début (`</Grid>`), indiquant que l’erreur est située à l’intérieur de l’objet `Grid`. Notez que l’étiquette de fermeture est manquante dans le deuxième objet `Button`. Une fois le `/` de fermeture ajouté, la liste du volet **Résultats** est mise à jour. Ces erreurs initiales sont à présent résolues, mais deux erreurs supplémentaires ont été identifiées.  

4. Double-cliquez sur « Le membre "contenu" n'est pas reconnu ou n'est pas accessible. ». Le `c` dans `content` devrait être en majuscules. Remplacez le « c » minuscule par un « c » majuscule.  

5. Double-cliquez sur « la propriété « Mame » n’existe pas dans le '<http://schemas.microsoft.com/winfx/2006/xaml>' espace de noms. » Le « M » dans « Mame » devrait être un « N ». Remplacez le « M » par un « N ». Maintenant que le code XAML peut être analysé, l'application s'affiche sur l'aire de conception.  

    ![Débogage de XAML dans Blend pour Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")  

    Appuyez sur Ctrl+Maj+B pour générer votre projet et vous assurer qu’il ne contient plus aucune erreur.  

## <a name="debugging-in-visual-studio"></a>Débogage dans Visual Studio  
 Vous pouvez ouvrir les projets [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] dans Visual Studio afin de déboguer plus facilement le code dans votre application. Pour ouvrir un projet [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] dans Visual Studio, cliquez avec le bouton droit dans le volet **Projets**, puis cliquez sur **Modifier dans Visual Studio**. Une fois la session de débogage terminée dans Visual Studio, appuyez sur Ctrl+Maj+S pour enregistrer toutes vos modifications, puis revenez à [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Vous êtes alors invité à recharger le projet. Cliquez sur **Oui pour tout** pour poursuivre votre travail dans [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  

 Pour plus d’informations sur le débogage de votre application, consultez [UWP de déboguer des applications dans Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  

## <a name="getting-help"></a>Obtenir de l’aide  
 Si vous avez besoin d’aide plus débogage votre [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] application, vous pouvez rechercher le [forums des Communautés application UWP](http://go.microsoft.com/fwlink/?LinkId=280308) pour les publications relatives à votre problème ou poser une question.

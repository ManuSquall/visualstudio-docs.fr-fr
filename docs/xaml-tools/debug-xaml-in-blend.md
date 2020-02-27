---
title: Déboguer du code XAML dans Blend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 04bd4540de47ec8a9da86069acb33770f9c800b8
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706370"
---
# <a name="debug-xaml-in-blend"></a>Déboguer XAML dans Blend

Vous pouvez utiliser les outils de Blend pour Visual Studio pour déboguer le code XAML dans votre application. Lors de la création d’un projet, toutes les erreurs sont affichées dans le volet **Résultats**. Double-cliquez sur une erreur pour localiser le balisage associé à l'erreur. Si vous avez besoin de davantage d’espace pour travailler, vous pouvez masquer le panneau **résultats** en appuyant sur **F12**.

## <a name="syntax-errors"></a>Erreurs de syntaxe

Des erreurs de syntaxe se produisent si votre code XAML, ou les fichiers code-behind ne suivent pas les règles de mise en forme du langage. La description de l’erreur peut vous aider à la résoudre. La liste spécifie également le nom du fichier et le numéro de ligne où l’erreur se produit. Les erreurs XAML sont répertoriées dans l’onglet **Balisage** du volet **Résultats**.

> [!TIP]
> XAML est un langage de balisage basé sur XML qui suit les règles de syntaxe de XML.

Certaines causes courantes d’erreurs de syntaxe XAML se présentent comme suit :

- Un mot clé n’a pas été correctement orthographié ou la casse est erronée.

- Des guillemets sont manquants autour d'attributs ou de chaînes de texte.

- Il manque une étiquette de fermeture à un élément XAML.

- Il existe un élément XAML à un emplacement non autorisé.

Pour plus d’informations sur la syntaxe XAML de base, consultez la page [Guide de base de la syntaxe XAML](/windows/uwp/xaml-platform/xaml-syntax-guide).

Vous pouvez également identifier et résoudre les erreurs de syntaxe code-behind simples, les erreurs de compilation et les erreurs d’exécution dans Blend. Toutefois, il peut être plus facile d'identifier et de résoudre les erreurs code-behind dans Visual Studio.

### <a name="debugging-sample-xaml-code"></a>Débogage d'un exemple de code XAML

L’exemple suivant vous guide à travers une session de débogage XAML simple dans Blend.

#### <a name="to-create-a-project"></a>Pour créer un projet

1. Dans Blend, ouvrez le menu **fichier** , puis cliquez sur **nouveau projet**.

    Dans la boîte de dialogue **Nouveau projet**, une liste de types de projet apparaît sur le côté gauche. Lorsque vous cliquez sur un type de projet, les modèles de projet associés à ce type apparaissent sur le côté droit.

2. Dans la liste des types de projets, cliquez sur **Windows universel**.

3. Dans la liste des modèles de projet, cliquez sur **application vide (Windows universel)** .

4. Dans la zone de texte **nom** , tapez `DebuggingSample`.

5. Dans la zone de texte **Emplacement**, vérifiez l’emplacement du projet.

6. Dans la liste **Langage**, cliquez sur **Visual C#** , puis sur **OK** pour créer le projet.

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

10. Appuyez sur **Ctrl**+**MAJ**+**B** pour générer le projet.

    Un message d’erreur s’affiche vous indiquant que le projet ne peut pas être généré et le volet **Résultats** listant les erreurs apparaît au bas de l’application.

    ![Déboguer du XAML dans Blend pour Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>Résoudre les erreurs XAML

Quand des erreurs XAML sont détectées, l'aire de conception affiche une alerte indiquant que votre projet contient un balisage non valide. Au fur et à mesure de la résolution des erreurs, la liste d’erreurs dans le volet **Résultats** est mise à jour. Quand vous avez résolu toutes les erreurs, l'aire de conception est activée et votre application y est affichée.

#### <a name="to-resolve-the-xaml-errors"></a>Pour résoudre les erreurs XAML

1. Double-cliquez sur la première erreur de la liste. La description est « la valeur «< » n’est pas valide dans un attribut.» Lorsque vous double-cliquez sur l'erreur, le pointeur trouve l'emplacement correspondant dans le code. Le `<` est valide, étant placé devant `Button` et non pas devant un attribut, comme indiqué dans le message d'erreur. Si vous examinez la ligne de code précédente, vous remarquez que le guillemet anglais fermant de l'attribut `Top` est manquant. Tapez le guillemet anglais fermant. Notez que la liste d’erreurs dans le volet **Résultats** est mise à jour au fur et à mesure de vos modifications.

2. Double-cliquez sur la description « 0 » n’est pas valide au début d’un nom.» `Margin="0,149,0,0"` semble bien formée. Toutefois, notez que le codage en couleur de `Margin` n'est pas le même que celui des autres instances de `Margin` dans le code. L'absence de guillemets anglais fermants dans la paire nom/valeur précédente (`VerticalAlignment="Top`) fait que `Margin="` est lu comme faisant partie de la valeur de l'attribut précédent, et 0 est lu comme le début de la paire nom/ valeur. Tapez le guillemet anglais fermant pour `Top`. La liste d’erreurs dans le volet **Résultats** est mise à jour au fur et à mesure de vos modifications.

3. Double-cliquez sur l'erreur restante : « Le Bouton de balise XML de fermeture ne correspond pas » Le pointeur se trouve sur la balise **Grid** de début (`</Grid>`), indiquant que l’erreur est située à l’intérieur de l’objet `Grid`. Notez que l’étiquette de fermeture est manquante dans le deuxième objet `Button`. Une fois le `/` de fermeture ajouté, la liste du volet **Résultats** est mise à jour. Ces erreurs initiales sont à présent résolues, mais deux erreurs supplémentaires ont été identifiées.

4. Double-cliquez sur « Le membre "contenu" n'est pas reconnu ou n'est pas accessible. ». Le `c` dans `content` devrait être en majuscules. Remplacez le « c » minuscule par un « c » majuscule.

5. Double-cliquez sur « la propriété’mame’n’existe pas dans l’espace de noms `http://schemas.microsoft.com/winfx/2006/xaml` ». Le « M » dans « Mame » devrait être un « N ». Remplacez le « M » par un « N ». Maintenant que le code XAML peut être analysé, l'application s'affiche sur l'aire de conception.

    ![Débogage XAML dans Blend pour Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Appuyez sur **Ctrl**+**MAJ**+**B** pour générer votre projet et confirmer qu’il n’y a pas d’erreurs restantes.

## <a name="debug-in-visual-studio"></a>Déboguer dans Visual Studio

Vous pouvez ouvrir Blend Projects dans Visual Studio pour déboguer plus facilement le code dans votre application. Pour ouvrir un projet Blend dans Visual Studio, cliquez avec le bouton droit sur le projet dans le panneau **projets** , puis cliquez sur **modifier dans Visual Studio**. Une fois que vous avez terminé votre session de débogage dans Visual Studio, appuyez sur Ctrl + Maj + S pour enregistrer toutes vos modifications, puis revenez à Blend. Vous êtes alors invité à recharger le projet. Cliquez sur **Oui pour tout** pour continuer à travailler dans Blend.

Pour plus d’informations sur le débogage de votre application, consultez [Déboguer des applications UWP dans Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Obtenir de l'aide

Si vous avez besoin d’aide supplémentaire sur le débogage de votre application Blend, vous pouvez rechercher des publications relatives à votre problème sur les forums de la [communauté d’applications UWP](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) ou publier une question.

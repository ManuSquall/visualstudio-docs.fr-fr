---
title: Comment utiliser le thème foncé et modifier la couleur du texte dans Visual Studio
description: Découvrez comment définir le thème de couleur Visual Studio par défaut en mode Dark et modifier les couleurs de police dans l’éditeur de texte.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperfq1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec0015f6abd434884d039407209d741febd41121
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711714"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-text-editor"></a>Comment : personnaliser l’éditeur de texte et l’IDE Visual Studio

Dans cet article de procédure, nous allons personnaliser le thème de couleur de Visual Studio en sélectionnant le thème sombre. Nous allons également personnaliser les couleurs de deux types de texte différents dans l’éditeur de texte.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range=">=vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Définir le thème de couleur de l’IDE

Le thème de couleur par défaut de l’interface utilisateur de Visual Studio se nomme **Bleu**. Nous allons le remplacer par le thème **Dark** (Sombre).

1. Dans la barre de menus, qui est la rangée de menus tels que **Fichier** et **Edition**, choisissez **Outils** > **Options**.

1. Dans la **Environment**  >  page options**générales** de l’environnement, remplacez la sélection du **thème de couleur** par **foncé**, puis cliquez sur **OK**.

   Le thème de couleur de tout l’environnement de développement (IDE) Visual Studio change et devient **Sombre**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 en thème sombre](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 en thème sombre](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Vous pouvez installer d’autres thèmes prédéfinis en téléchargeant et en installant **l’éditeur de thème de couleur de Visual Studio** à partir de la [Place de marché Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Après avoir installé cet outil, des thèmes de couleurs supplémentaires s’affichent dans la liste déroulante **thème de couleurs** .

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Vous pouvez créer vos propres thèmes en installant le **Concepteur de thèmes de couleurs Visual Studio** à partir de la [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-color"></a>Modifier la couleur du texte

Nous allons maintenant personnaliser des couleurs de texte dans l’éditeur. Tout d’abord, créons un fichier XML pour voir les couleurs par défaut.

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **fichier**.

1. Dans la boîte de dialogue **Nouveau fichier**, sous la catégorie **Général**, choisissez **Fichier XML**, puis **Ouvrir**.

1. Collez le fichier XML ci-dessous sous la ligne contenant `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Notez que les numéros de ligne s’affichent en turquoise et que les attributs XML (tels que `id="bk101"`) s’affichent en bleu clair. Nous allons changer la couleur de texte de ces éléments.

   ![Couleurs de police du fichier XML](media/quickstart-personalize-xml-file.png)

1. Pour ouvrir la boîte de dialogue **Options**, choisissez **Outils** > **Options** dans la barre de menus.

1. Sous **Environnement**, choisissez la catégorie **Polices et couleurs**.

   Notez que le texte sous **Afficher les paramètres de** indique **Éditeur de texte**&mdash; et c’est ce que nous voulons. Développez la liste déroulante pour voir la liste étendue d’emplacements où vous pouvez personnaliser les polices et la couleur du texte.

1. Pour changer la couleur du texte des numéros de ligne, dans la liste **Afficher les éléments**, sélectionnez **Numéro de ligne**. Dans la zone **Premier plan de l’élément**, choisissez **Olive**.

   ![Boîte de dialogue Options, catégorie Polices et couleurs](media/quickstart-personalize-line-number-color.png)

   Certains langages ont leurs propres paramètres de polices et de couleurs. Si vous développez en C++ et que vous souhaitez changer la couleur utilisée pour les fonctions par exemple, recherchez **Fonctions C++** dans la liste **Afficher les éléments**.

1. Avant de fermer la boîte de dialogue, changeons aussi la couleur des attributs XML. Dans la liste **Afficher les éléments**, sélectionnez **Attribut XML**. Dans la zone **Premier plan de l’élément**, choisissez **Vert clair**. Sélectionnez **OK** pour enregistrer nos sélections et fermer la boîte de dialogue.

   Les numéros de ligne s’affichent désormais en couleur olive et les attributs XML s’affichent désormais en vert clair. Si vous ouvrez un autre type de fichier, comme un fichier de code C++ ou C#, vous remarquerez que les numéros de ligne s’affichent aussi en couleur olive.

   ![Fichier XML avec nouvelles couleurs de police](media/quickstart-personalize-xml-file-new-colors.png)

Nous avons seulement exploré deux façons de personnaliser les couleurs dans Visual Studio. Nous espérons que vous explorerez les autres options de personnalisation dans la boîte de dialogue **Options** pour réellement vous familiariser avec Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Modifier les polices, les couleurs et les options de contraste élevé dans Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Personnaliser l’éditeur](../ide/how-to-change-text-case-in-the-editor.md)
- [Vue d’ensemble de l’IDE Visual Studio](../get-started/visual-studio-ide.md)

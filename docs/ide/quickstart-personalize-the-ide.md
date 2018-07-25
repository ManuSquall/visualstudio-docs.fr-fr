---
title: Définir le thème de couleur et les polices dans Visual Studio
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9132547055ef17e4ecd28274a0b1a3de7dd8ce2
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078223"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Démarrage rapide : personnaliser l’éditeur et l’IDE de Visual Studio

Dans ce guide de démarrage rapide qui dure entre 5 et 10 minutes, nous allons personnaliser le thème de couleur de Visual Studio et deux couleurs de texte dans l’éditeur de texte.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="set-the-color-theme"></a>Définir le thème de couleur

Le thème de couleur par défaut de l’interface utilisateur de Visual Studio 2017 se nomme **Bleu**. Nous allons le remplacer par le thème **Dark** (Sombre).

1. Dans la barre de menus, qui est la rangée de menus tels que **Fichier** et **Edition**, choisissez **Outils** > **Options**.

1. Dans la page **Environnement** > **Options générales**, remplacez la sélection du **Thème de couleur** par **Sombre**, puis choisissez **OK**.

   Le thème de couleur de l’environnement de développement (IDE) Visual Studio entier change et devient **Sombre**.

   ![VS dans le thème Sombre](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Vous pouvez installer d’autres thèmes prédéfinis en téléchargeant et en installant **l’éditeur de thème de couleur de Visual Studio** à partir de la [place de marché Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Une fois cet outil installé, d’autres thèmes de couleurs apparaissent dans la liste déroulante des **thèmes de couleurs**.

## <a name="change-text-color"></a>Modifier la couleur du texte

Nous allons maintenant personnaliser des couleurs de texte dans l’éditeur. Tout d’abord, créons un fichier XML pour voir les couleurs par défaut.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Fichier**.

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

   Notez que le texte sous **Afficher les paramètres de** indique **Éditeur de texte** &mdash; et c’est ce que nous voulons. Développez la liste déroulante pour voir la liste étendue d’emplacements où vous pouvez personnaliser les polices et la couleur du texte.

1. Pour changer la couleur du texte des numéros de ligne, dans la liste **Afficher les éléments**, sélectionnez **Numéro de ligne**. Dans la zone **Premier plan de l’élément**, choisissez **Olive**.

   ![Boîte de dialogue Options, catégorie Polices et couleurs](media/quickstart-personalize-line-number-color.png)

   Certains langages ont leurs propres paramètres de polices et de couleurs. Si vous développez en C++ et que vous souhaitez changer la couleur utilisée pour les fonctions par exemple, recherchez **Fonctions C++** dans la liste **Afficher les éléments**.

1. Avant de fermer la boîte de dialogue, changeons aussi la couleur des attributs XML. Dans la liste **Afficher les éléments**, sélectionnez **Attribut XML**. Dans la zone **Premier plan de l’élément**, choisissez **Vert clair**. Sélectionnez **OK** pour enregistrer nos sélections et fermer la boîte de dialogue.

   Les numéros de ligne s’affichent désormais en couleur olive et les attributs XML s’affichent désormais en vert clair. Si vous ouvrez un autre type de fichier, comme un fichier de code C++ ou C#, vous remarquerez que les numéros de ligne s’affichent aussi en couleur olive.

   ![Fichier XML avec nouvelles couleurs de police](media/quickstart-personalize-xml-file-new-colors.png)

Nous avons seulement exploré deux façons de personnaliser les couleurs dans Visual Studio. Nous espérons que vous explorerez les autres options de personnalisation dans la boîte de dialogue **Options** pour réellement vous familiariser avec Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : premier aperçu de l'IDE Visual Studio](../ide/quickstart-ide-orientation.md)
- [Démarrage rapide : codage dans l’éditeur](../ide/quickstart-editor.md)
- [Démarrage rapide : projets et solutions](../ide/quickstart-projects-solutions.md)
- [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md)
- [Personnaliser l’éditeur](../ide/customizing-the-editor.md)
- [Vue d’ensemble de l’IDE Visual Studio](../ide/visual-studio-ide.md)

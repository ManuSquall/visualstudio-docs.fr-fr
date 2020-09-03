---
title: 'Comment : utiliser des extraits XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4998fbc530cf4350f4a64b0fd527e0764eafce27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656260"
---
# <a name="how-to-use-xml-snippets"></a>Procédure : utiliser des extraits XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez invoquer des extraits XML en utilisant les deux commandes suivantes du menu contextuel de l'éditeur XML. La commande **Insérer un extrait** insère l’extrait XML à la position du curseur. La commande **entourer de** encapsule l’extrait XML autour du texte sélectionné. Chaque extrait XML possède des types d'extrait désignés. Les types d’extraits déterminent si l’extrait de code est disponible avec la commande **Insérer un extrait** , la commande **entourer de** ou les deux.

 Une fois l'extrait XML ajouté à l'éditeur, tous ses champs modifiables sont surlignés en jaune et le curseur est placé dans le premier d'entre eux.

## <a name="insert-snippet"></a>Insérer un extrait
 Les procédures suivantes décrivent comment accéder à la commande **Insérer un extrait** .

> [!NOTE]
> La commande **Insérer un extrait** de code est également disponible via le raccourci clavier (Ctrl + K, puis Ctrl + X).

#### <a name="to-insert-snippets-from-the-shortcut-menu"></a>Pour insérer des extraits à partir du menu contextuel

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Cliquez avec le bouton droit et sélectionnez **Insérer un extrait**.

     Une liste des extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.

#### <a name="to-insert-snippets-using-the-intellisense-menu"></a>Pour insérer des extraits à l'aide du menu IntelliSense

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Dans le menu **Edition** , pointez sur **IntelliSense**, puis sélectionnez **Insérer un extrait**.

     Une liste des extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.

#### <a name="to-insert-snippets-through-the-intellisense-complete-word-list"></a>Pour insérer des extraits via la liste de remplissage IntelliSense

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Commencez à entrer l'extrait XML à ajouter à votre fichier. Si le remplissage automatique est activé, la liste de remplissage IntelliSense s'affiche. Dans le cas contraire, appuyez sur CTRL+ESPACE pour l'activer.

3. Sélectionnez l'extrait XML dans la liste de remplissage.

4. Appuyez sur TAB à deux reprises pour invoquer l'extrait XML.

> [!NOTE]
> Parfois, l'extrait XML n'est pas invoqué. Par exemple, si vous tentez d'insérer un élément `xs:complexType` dans un nœud `xs:element`, l'éditeur ne génère aucun extrait XML. En effet, lorsqu'un élément `xs:complexType` est utilisé à l'intérieur d'un nœud `xs:element`, aucun attribut ni sous-élément n'est requis, de sorte que l'éditeur n'a aucune donnée à insérer.

#### <a name="to-insert-snippets-using-the-shortcut-name"></a>Pour insérer des extraits à l'aide du nom raccourci

1. Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.

2. Entrez `<` dans le volet de l'éditeur.

3. Appuyez sur ÉCHAP pour fermer la liste de remplissage IntelliSense.

4. Entrez le nom raccourci de l'extrait XML, puis appuyez sur TAB pour l'invoquer.

## <a name="surround-with"></a>Entourer de
 Les procédures suivantes décrivent comment accéder à la commande **surround** .

> [!NOTE]
> La commande **entourer de** est également disponible via le raccourci clavier (Ctrl + K, puis Ctrl + S).

#### <a name="to-use-surround-with-from-the-context-menu"></a>Pour utiliser la commande Entourer de du menu contextuel

1. Sélectionnez le texte à entourer dans l'éditeur XML.

2. Cliquez avec le bouton droit et sélectionnez **entourer de**.

     Une liste des encadrements d'extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.

#### <a name="to-use-surround-with-from-the-intellisense-menu"></a>Pour utiliser un encadrement à partir du menu Intellisense

1. Sélectionnez le texte à entourer dans l'éditeur XML.

2. Dans le menu **Edition** , pointez sur **IntelliSense**, puis sélectionnez **entourer de**.

     Une liste des encadrements d'extraits XML disponibles s'affiche.

3. Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.

## <a name="using-xml-snippets"></a>Utilisation d'extraits XML
 Une fois que vous avez choisi un extrait XML, le texte de cet extrait de code est automatiquement inséré à l'emplacement du curseur. Tous les champs modifiables contenus dans l'extrait sont surlignés et le premier de ces champs est automatiquement sélectionné. Le champ actuellement sélectionné est encadré.

 Après avoir sélectionné un champ, vous pouvez y entrer une nouvelle valeur. La touche TAB permet de parcourir en boucle les champs modifiables de l'extrait ; les touches MAJ+TAB effectuent le même parcours dans l'ordre inverse. Cliquer dans un champ place le curseur dans ce champ ; double-cliquer sur un champ permet de le sélectionner. Lorsqu'un champ est en évidence, une info-bulle peut s'afficher pour le décrire.

 Seule la première instance d'un champ donné est modifiable. Lorsque ce champ est surligné, les autres instances du même champ sont mises en évidence. Lorsque vous modifiez la valeur d'un champ modifiable, ce champ change partout où il est utilisé dans l'extrait.

 Appuyez sur ENTRÉE ou sur ÉCHAP pour annuler la modification du champ et revenir au mode normal de l'éditeur.

 Les couleurs par défaut des champs d’extrait de code modifiables peuvent être modifiées en modifiant le paramètre champ d’extrait de code dans le volet **polices et couleurs** de la boîte de dialogue **options** . Pour plus d’informations, consultez [Comment : modifier les polices et les couleurs dans l’éditeur](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Voir aussi
 [Extraits XML](../xml-tools/xml-snippets.md) [Comment : générer un extrait XML à partir d’un schéma XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md) [Comment : créer des extraits XML](../xml-tools/how-to-create-xml-snippets.md)

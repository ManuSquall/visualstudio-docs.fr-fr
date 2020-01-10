---
title: Encodages et caractères de saut de ligne
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588588"
---
# <a name="encodings-and-line-endings"></a>Encodages et fins de ligne

Les caractères suivants sont interprétés comme des sauts de ligne dans Visual Studio :

- CR LF : retour chariot + saut de ligne, caractères Unicode 000D + 000A

- LF : saut de ligne, caractère Unicode 000A

- NEL : ligne suivante, caractère Unicode 0085

- LS : séparateur de ligne, caractère Unicode 2028

- PS : séparateur de paragraphe, caractère Unicode 2029

Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.

Quand vous ouvrez un fichier contenant des caractères de saut de ligne différents, vous pouvez voir s’afficher une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.

## <a name="advanced-save-options"></a>Options d'enregistrement avancées

Vous pouvez utiliser la boîte de dialogue **Fichier** > **Options d’enregistrement avancées** pour spécifier le type de caractères de saut de ligne souhaité. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.

![Boîte de dialogue Options d’enregistrement avancées](media/line_endings.png)

> [!NOTE]
> Si vous ne voyez pas la commande **Options d’enregistrement avancées** dans le menu **Fichier**, vous pouvez l’ajouter. Choisissez **Outils**, **personnaliser**, puis l’onglet **commandes** . Dans la liste déroulante **barre de menus** , choisissez **fichier**, puis cliquez sur le bouton **Ajouter une commande** . Dans la boîte de dialogue **Ajouter une commande**, sous **Catégories**, choisissez **Fichier** et, dans la liste **Commandes**, choisissez **Options d’enregistrement avancées**. Choisissez **OK** , puis cliquez sur **le bouton descendre pour déplacer la** commande vers n’importe quel emplacement dans le menu. Choisissez **Fermer** pour fermer la boîte de dialogue **Personnaliser**. Pour plus d’informations, consultez [Personnaliser les menus et les barres d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Vous pouvez aussi accéder à la boîte de dialogue **Options d’enregistrement avancées** en choisissant **Fichier** > **Enregistrer le \<fichier\> sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, choisissez la flèche de liste déroulante à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec encodage**.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)

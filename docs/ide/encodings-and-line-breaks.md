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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59ed38c28c6818fb618156450d47c05b4f35d63d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978162"
---
# <a name="encodings-and-line-endings"></a>Encodages et fins de ligne

Les caractères suivants sont interprétés comme des sauts de ligne dans Visual Studio :

- CR LF : Retour chariot + saut de ligne, caractères Unicode 000D + 000A

- LF : Saut de ligne, caractère Unicode 000A

- NEL : Ligne suivante, caractère Unicode 0085

- LS : Séparateur de ligne, caractère Unicode 2028

- PS : Séparateur de paragraphe, caractère Unicode 2029

Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.

Quand vous ouvrez un fichier contenant des caractères de saut de ligne différents, vous pouvez voir s’afficher une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.

## <a name="advanced-save-options"></a>Options d'enregistrement avancées

Vous pouvez utiliser la boîte de dialogue **Fichier** > **Options d’enregistrement avancées** pour spécifier le type de caractères de saut de ligne souhaité. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.

![Boîte de dialogue Options d’enregistrement avancées](media/line_endings.png)

> [!NOTE]
> Si vous ne voyez pas la commande **Options d’enregistrement avancées** dans le menu **Fichier**, vous pouvez l’ajouter. Choisissez **Outils**, **Personnaliser**, puis choisissez l’onglet **Commandes**. Dans la liste déroulante **Barre de menus**, choisissez **Fichier**, puis le bouton **Ajouter une commande**. Dans la boîte de dialogue **Ajouter une commande**, sous **Catégories**, choisissez **Fichier** et, dans la liste **Commandes**, choisissez **Options d’enregistrement avancées**. Choisissez **OK**, puis choisissez le bouton **Descendre** pour déplacer la commande à l’emplacement souhaité dans le menu. Choisissez **Fermer** pour fermer la boîte de dialogue **Personnaliser**. Pour plus d’informations, consultez [Personnaliser les menus et les barres d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Vous pouvez aussi accéder à la boîte de dialogue **Options d’enregistrement avancées** en choisissant **Fichier** > **Enregistrer le \<fichier\> sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, choisissez la flèche de liste déroulante à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec encodage**.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
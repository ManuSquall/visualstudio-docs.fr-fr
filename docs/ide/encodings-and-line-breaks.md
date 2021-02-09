---
title: Encodages et caractères de saut de ligne
description: Découvrez les caractères que Visual Studio interprète comme des sauts de ligne et comment les caractères d’encodage et de saut de ligne d’origine sont conservés.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e466439469db66e8e871115abc9828988f24b546
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924749"
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

Vous pouvez **utiliser la**  >  boîte de dialogue **options d’enregistrement avancées** pour déterminer le type de caractère de saut de ligne souhaité. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.

![Options d'enregistrement avancées (boîte de dialogue)](media/line_endings.png)

> [!NOTE]
> Si vous ne voyez pas la commande **Options d’enregistrement avancées** dans le menu **Fichier**, vous pouvez l’ajouter. 
> 1. Choisissez **Outils**, **personnaliser**, 
> 1. Choisissez l’onglet **commandes** , sélectionnez la case d’option **barre de menus** et dans la liste déroulante correspondante, choisissez **fichier**. Choisissez le bouton **Ajouter une commande** . 
> 1. Dans la boîte de dialogue **Ajouter une commande**, sous **Catégories**, choisissez **Fichier** et, dans la liste **Commandes**, choisissez **Options d’enregistrement avancées**. Cliquez sur le bouton **OK** .
> 1. Utilisez les boutons **monter** et **descendre** pour déplacer la commande vers n’importe quel emplacement dans le menu. Choisissez **Fermer** pour fermer la boîte de dialogue **Personnaliser**. 
> Pour plus d’informations, consultez [Personnaliser les menus et les barres d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Vous pouvez également accéder à la boîte de dialogue **options d’enregistrement avancées** en choisissant **fichier**  >  **Enregistrer \<file\> sous**. Dans la boîte de dialogue **enregistrer le fichier sous** , choisissez le triangle déroulant en regard du bouton **Enregistrer** , puis choisissez **enregistrer avec encodage**.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)

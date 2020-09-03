---
title: Guide pratique pour gérer le retour automatique à la ligne dans l’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59cc8536707744543490bc3e91b85545e4cd4007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668851"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Guide pratique pour gérer le retour automatique à la ligne dans l'éditeur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous pouvez activer et désactiver l’option **Retour automatique à la ligne**. Lorsque cette option est activée, la partie d’une longue ligne qui s’étend au-delà de la largeur de la fenêtre de l’éditeur de code s’affiche à la ligne suivante. Lorsque cette option est désactivée, par exemple, pour faciliter l’utilisation de la numérotation des lignes, vous pouvez faire défiler l’affichage vers la droite pour voir l’extrémité des longues lignes.

 Pour plus d’informations, consultez [Guide pratique pour définir les options générales de l’éditeur](https://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans **l’aide** en fonction de vos paramètres actifs ou de l’édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="procedure"></a>Procédure

#### <a name="to-set-word-wrap-preferences"></a>Pour définir les préférences de retour automatique à la ligne

1. Dans le menu **Tools** (Outils), sélectionnez **Options**.

2. Dans le dossier **Éditeur de texte**, choisissez les options **Général** dans le sous-dossier **Tous les langages** pour définir cette option globalement.

     — ou —

     Choisissez les options **Général** dans le sous-dossier du langage dans lequel vous programmez.

3. Sous **Paramètres**, activez ou désactivez l’option **Retour automatique à la ligne**.

     Lorsque l’option **Retour automatique à la ligne** est sélectionnée, l’option **Afficher des glyphes visuels pour le retour automatique à la ligne** est activée.

4. Sélectionnez l’option **Afficher des glyphes visuels pour le retour automatique à la ligne** si vous préférez afficher un indicateur fléché de retour là où une longue ligne est automatiquement renvoyée à une deuxième ligne. Désactivez cette option si vous préférez ne pas afficher d’indicateurs fléchés.

    > [!NOTE]
    > Ces flèches de rappel ne sont pas ajoutées à votre code : elles sont utilisées uniquement à des fins d’affichage.

## <a name="see-also"></a>Voir aussi
 [Personnalisation de la boîte de dialogue Options de l’éditeur de texte de l’éditeur](../../ide/customizing-the-editor.md) [Text Editor Options Dialog Box](../../ide/reference/text-editor-options-dialog-box.md) [écriture du code](../../ide/writing-code-in-the-code-and-text-editor.md)

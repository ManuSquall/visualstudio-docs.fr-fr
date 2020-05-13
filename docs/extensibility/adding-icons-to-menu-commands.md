---
title: Ajout d’icônes aux commandes de menus ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740155"
---
# <a name="add-icons-to-menu-commands"></a>Ajouter des icônes aux commandes de menu
Les commandes peuvent apparaître sur les menus et les barres d’outils. Sur les barres d’outils, il est courant qu’une commande soit affichée avec juste une icône (pour économiser de l’espace) tandis que sur les menus une commande apparaît généralement à la fois avec une icône et un texte.

 Les icônes sont de 16 pixels de large par 16 pixels de haut et peuvent être soit 8 bits de profondeur de couleur (256 couleurs) ou 32 bits de profondeur de couleur (vraie couleur). Les icônes de couleur 32 bits sont préférées. Les icônes sont généralement disposées en une seule ligne horizontale dans une seule bitmap, bien que plusieurs bitmaps soient autorisés. Ce bitmap est déclaré dans le fichier *.vsct* avec les icônes individuelles disponibles dans la bitmap. Voir la référence pour [l’élément Bitmaps](../extensibility/bitmaps-element.md) pour plus de détails.

## <a name="add-an-icon-to-a-command"></a>Ajouter une icône à une commande
 La procédure suivante suppose que vous avez un projet VSPackage existant avec une commande de menu. Pour savoir comment le faire, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Créez une bitmap avec une profondeur de couleur de 32 bits. Une icône est toujours 16 x 16 donc cette bitmap doit être de 16 pixels de haut et un multiple de 16 pixels de large.

     Chaque icône est placée sur la bitmap côte à côte dans une seule rangée. Utilisez le canal alpha pour indiquer les lieux de transparence dans chaque icône.

     Si vous utilisez une profondeur de couleur 8 `RGB(255,0,255)`bits, utilisez magenta, , comme la transparence. Cependant, les icônes de couleur 32 bits sont préférées.

2. Copiez le fichier d’icônes à l’annuaire *Ressources* dans votre projet VSPackage. Dans la **Solution Explorer**, ajouter l’icône au projet. (Sélectionnez **ressources**, et sur le menu contextuellez **Ajouter,** puis **élément existant**, et sélectionnez votre fichier d’icône.)

3. Ouvrez le fichier *.vsct* dans l’éditeur.

4. Ajouter `GuidSymbol` un élément avec un nom de **testIcon**. Créez un GUID **(Outils** > **Créez GUID**, puis sélectionnez le `value` format de **registre** et cliquez sur **Copie**) et collez-le dans l’attribut. Le résultat devrait ressembler à ceci:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Ajoutez `<IDSymbol>` un pour l’icône. L’attribut `name` est l’ID de `value` l’icône, et l’indique sa position sur la bande, le cas échéant. S’il n’y a qu’une seule icône, ajoutez-en 1. Le résultat devrait ressembler à ceci:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Créez `<Bitmap>` un `<Bitmaps>` dans la section du fichier *.vsct* pour représenter la bitmap contenant les icônes.

    - Définissez `guid` la valeur au `<GuidSymbol>` nom de l’élément que vous avez créé dans l’étape précédente.

    - Définissez `href` la valeur sur le chemin relatif du fichier bitmap (dans ce cas **Ressources\\<nom\>de fichier d’icône**.

    - Définissez `usedList` la valeur de l’IDSymbol que vous avez créé plus tôt. Cet attribut spécifie une liste de virgules des icônes à utiliser dans le VSPackage. Les icônes qui ne figurent pas sur la liste sont exclues de la compilation de formulaires.

         Le bloc Bitmap devrait ressembler à ceci:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Dans l’élément existant, `<Button>` définissez l’élément `Icon` sur les valeurs GUIDSymbol et IDSymbol que vous avez créées précédemment. Voici un exemple d’élément Bouton avec ces valeurs :

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testez votre icône. Générez le projet et commencez le débogage. Dans le cas expérimental, trouvez la commande. Il doit montrer l’icône que vous avez ajoutée.

## <a name="see-also"></a>Voir aussi
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [VSCT XML référence schéma](../extensibility/vsct-xml-schema-reference.md)

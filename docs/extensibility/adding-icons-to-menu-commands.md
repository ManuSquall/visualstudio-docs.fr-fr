---
title: Ajout d’icônes à des commandes de menu | Microsoft Docs
description: Découvrez comment ajouter des icônes à des commandes qui peuvent apparaître dans les menus et les barres d’outils de l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9f37bd14ed43ab0e165346f8ce09512c3981177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934362"
---
# <a name="add-icons-to-menu-commands"></a>Ajouter des icônes aux commandes de menu
Les commandes peuvent apparaître dans les menus et les barres d’outils. Dans les barres d’outils, il est courant qu’une commande s’affiche avec simplement une icône (pour économiser de l’espace) tandis que dans les menus, une commande apparaît généralement avec une icône et un texte.

 Les icônes sont de 16 pixels de large par 16 pixels de haut et peuvent avoir une profondeur de couleur de 8 bits (256 couleurs) ou une profondeur de couleur de 32 bits (couleur vraie). les icônes de couleur 32 bits sont préférées. Les icônes sont généralement organisées en une seule ligne horizontale dans une seule bitmap, bien que plusieurs bitmaps soient autorisées. Cette image bitmap est déclarée dans le fichier *. vsct* avec les icônes individuelles disponibles dans le bitmap. Pour plus d’informations, consultez la référence de l' [élément bitmaps](../extensibility/bitmaps-element.md) .

## <a name="add-an-icon-to-a-command"></a>Ajouter une icône à une commande
 La procédure suivante suppose que vous disposez d’un projet VSPackage existant avec une commande de menu. Pour savoir comment procéder, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Créez une image bitmap avec une profondeur de couleur de 32 bits. Une icône est toujours 16 x 16, ce qui signifie que cette bitmap doit avoir une hauteur de 16 pixels et un multiple de 16 pixels de large.

     Chaque icône est placée sur l’image bitmap à côté les unes des autres sur une seule ligne. Utilisez le canal alpha pour indiquer les emplacements de transparence dans chaque icône.

     Si vous utilisez une profondeur de couleur de 8 bits, utilisez le magenta, `RGB(255,0,255)` , comme transparence. Toutefois, les icônes de couleur 32 bits sont préférées.

2. Copiez le fichier icône dans le répertoire *Resources* de votre projet VSPackage. Dans la **Explorateur de solutions**, ajoutez l’icône au projet. (Sélectionnez **ressources**, puis dans le menu contextuel, cliquez sur **Ajouter**, puis sur **élément existant**, et sélectionnez votre fichier d’icône.)

3. Ouvrez le fichier *. vsct* dans l’éditeur.

4. Ajoutez un `GuidSymbol` élément avec le nom **testIcon**. Créez un GUID (**Outils** de  >  **création de GUID**, sélectionnez le **format du Registre** , puis cliquez sur **copier**) et collez-le dans l' `value` attribut. Le résultat doit ressembler à ceci :

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Ajoutez un `<IDSymbol>` pour l’icône. L' `name` attribut est l’ID de l’icône et le `value` indique sa position sur la bande, le cas échéant. S’il n’y a qu’une seule icône, ajoutez 1. Le résultat doit ressembler à ceci :

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Créez un `<Bitmap>` dans la `<Bitmaps>` section du fichier *. vsct* pour représenter l’image bitmap contenant les icônes.

    - Définissez la `guid` valeur sur le nom de l' `<GuidSymbol>` élément que vous avez créé à l’étape précédente.

    - Définissez la `href` valeur sur le chemin d’accès relatif du fichier bitmap (dans ce cas, **resources \\<\> nom du fichier icône**.

    - Définissez la `usedList` valeur sur le IDSymbol que vous avez créé précédemment. Cet attribut spécifie une liste délimitée par des virgules des icônes à utiliser dans le VSPackage. Les icônes qui ne figurent pas dans la liste sont des formulaires exclus de la compilation.

         Le bloc bitmap doit se présenter comme suit :

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. Dans l' `<Button>` élément existant, définissez l' `Icon` élément sur les valeurs GUIDSymbol et IDSymbol que vous avez créées précédemment. Voici un exemple d’élément Button avec ces valeurs :

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Testez votre icône. Générez le projet et commencez le débogage. Dans l’instance expérimentale, recherchez la commande. Elle doit afficher l’icône que vous avez ajoutée.

## <a name="see-also"></a>Voir aussi
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [Référence du schéma XML VSCT](../extensibility/vsct-xml-schema-reference.md)

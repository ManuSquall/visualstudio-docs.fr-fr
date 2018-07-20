---
title: Ajouter des icônes aux commandes de Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d01e64915004eb21a92c21a67291dc4f034112d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155009"
---
# <a name="add-icons-to-menu-commands"></a>Ajouter des icônes aux commandes de menu
Commandes peuvent apparaître dans les menus et barres d’outils. Des barres d’outils, il est courant pour une commande à afficher avec une simple icône (pour économiser de l’espace) tout en les menus de qu'une commande apparaît généralement avec une icône et du texte.  
  
 Icônes sont de 16 pixels de large par 16 pixels de haut et peuvent être de couleurs 8 bits (256 couleurs) ou de profondeur de couleur 32 bits (couleurs vraies). icônes de couleur 32 bits sont préférables. Icônes sont généralement organisés en une seule ligne horizontale dans une seule bitmap, bien que plusieurs images bitmap sont autorisés. Cette image bitmap est déclarée dans le *.vsct* fichier, ainsi que des icônes disponibles dans l’image bitmap. Consultez la référence pour le [élément Bitmaps](../extensibility/bitmaps-element.md) pour plus d’informations.  
  
## <a name="add-an-icon-to-a-command"></a>Ajouter une icône à une commande  
 La procédure suivante suppose que vous avez un projet VSPackage existant avec une commande de menu. Pour savoir comment procéder, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Créer une image bitmap avec une profondeur de couleur de 32 bits. Une icône est toujours 16 x 16 cette bitmap doit donc être 16 pixels de haut et un multiple de 16 pixels.  
  
     Chaque icône est placée sur l’image bitmap à côté d’eux en une seule ligne. Utilisez le canal alpha pour indiquer les emplacements de transparence dans chaque icône.  
  
     Si vous utilisez une profondeur de couleurs 8 bits, utilisez magenta, `RGB(255,0,255)`, comme la transparence. Toutefois, les icônes de couleur 32 bits sont préférables.  
  
2.  Copiez le fichier icône dans le *ressources* répertoire dans votre projet VSPackage. Dans le **l’Explorateur de solutions**, l’icône d’ajout au projet. (Sélectionnez **ressources**et sur le menu contextuel, cliquez **ajouter**, puis **élément existant**, puis sélectionnez votre fichier d’icône.)  
  
3.  Ouvrez le *.vsct* fichier dans l’éditeur.  
  
4.  Ajouter un `GuidSymbol` élément avec un nom de **testIcon**. Créer un GUID (**outils** > **créer un GUID**, puis sélectionnez **au Format de Registre** et cliquez sur **copie**) et collez-le dans le `value` attribut. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Ajouter un `<IDSymbol>` pour l’icône. Le `name` attribut est l’ID de l’icône et le `value` indique sa position sur la bande, le cas échéant. S’il existe qu’une seule icône, ajoutez 1. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Créer un `<Bitmap>` dans le `<Bitmaps>` section de la *.vsct* fichier pour représenter la bitmap qui contient les icônes.  
  
    -   Définir le `guid` valeur sur le nom de la `<GuidSymbol>` élément que vous avez créé à l’étape précédente.  
  
    -   Définir le `href` valeur le chemin d’accès relatif du fichier bitmap (dans ce cas **ressources\\< nom du fichier icône\>**.  
  
    -   Définir le `usedList` valeur à la IDSymbol que vous avez créé précédemment. Cet attribut spécifie une liste délimitée par des virgules des icônes à utiliser dans le VSPackage. Icônes pas dans la liste sont exclus de formulaire compilation.  
  
         Le bloc de Bitmap doit ressembler à ceci :  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Dans l’espace `<Button>` élément, définissez la `Icon` élément aux valeurs GUIDSymbol et IDSymbol vous avez créé précédemment. Voici un exemple d’un élément de bouton avec ces valeurs :  
  
    ```xml  
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">  
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />  
        <Icon guid="testIcon" id="testIcon1" />  
        <Strings>  
            <ButtonText>My Command name</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
8.  Testez votre icône. Générez le projet et commencez le débogage. Dans l’instance expérimentale, recherchez la commande. Il doit afficher l’icône que vous avez ajouté.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Référence du schéma XML VSCT](../extensibility/vsct-xml-schema-reference.md)
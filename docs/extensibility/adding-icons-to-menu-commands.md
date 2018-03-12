---
title: "Ajouter des icônes aux commandes de Menu | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 06d90b5174cc9ff2d09d7ccba8b2f39bc1d2a077
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-icons-to-menu-commands"></a>Ajouter des icônes aux commandes de Menu
Les commandes peuvent apparaître dans les menus et barres d’outils. Des barres d’outils, il est courant pour une commande à afficher avec simplement sur une icône (pour économiser de l’espace) lors de menus, qu'une commande apparaît généralement avec une icône et le texte.  
  
 Icônes 16 pixels de large par 16 pixels de haut et peuvent être soit une profondeur de couleur de 8 bits (256 couleurs) 32 bits de couleurs (color true). icônes de couleur 32 bits sont préférables. En général, les icônes sont organisées dans une seule ligne horizontale dans une seule bitmap, même si plusieurs images sont autorisées. Cette image bitmap est déclarée dans le fichier .vsct, ainsi que les icônes individuels disponibles dans l’image bitmap. Consultez la référence pour le [Bitmaps élément](../extensibility/bitmaps-element.md) pour plus d’informations.  
  
## <a name="adding-an-icon-to-a-command"></a>Ajout d’une icône à une commande  
 La procédure suivante suppose que vous disposez d’un projet VSPackage existant avec une commande de menu. Pour savoir comment procéder, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Créer une image bitmap avec une profondeur de couleur de 32 bits. Une icône est toujours 16 x 16 pour cette image bitmap doit être de 16 pixels de haut et un multiple de 16 pixels.  
  
     Chaque icône est placée sur l’image bitmap à côté d’eux dans une seule ligne. Utilisez le canal alpha pour indiquer les emplacements de transparence de chaque icône.  
  
     Si vous utilisez une profondeur de couleur de 8 bits, utilisez à magenta, `RGB(255,0,255)`, comme la transparence. Toutefois, les icônes de couleur 32 bits sont préférables.  
  
2.  Copiez le fichier d’icône dans le répertoire de ressources dans votre projet VSPackage. Dans l’Explorateur de solutions, l’icône d’ajout au projet. (Sélectionner des ressources, dans le menu contextuel, cliquez sur Ajouter, puis sur un élément existant et sélectionnez votre fichier d’icône.)  
  
3.  Ouvrez le fichier .vsct dans l’éditeur.  
  
4.  Ajouter un `GuidSymbol` élément avec un nom de **testIcon**. Créer un GUID (**outils / Create GUID**, puis sélectionnez **Format du Registre** et cliquez sur Copier) et collez-le dans le `value` attribut. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Ajouter un `<IDSymbol>` de l’icône. Le `name` attribut est l’ID de l’icône et la `value` indique sa position sur la bande, le cas échéant. S’il existe qu’une icône, ajoute 1. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Créer un `<Bitmap>` dans la `<Bitmaps>` section du fichier .vsct pour représenter la bitmap qui contient les icônes.  
  
    -   Définir le `guid` valeur au nom de la `<GuidSymbol>` élément que vous avez créé à l’étape précédente.  
  
    -   Définir le `href` valeur le chemin d’accès relatif du fichier bitmap (dans ce cas **ressources\\< nom du fichier icône\>**.  
  
    -   Définir le `usedList` valeur à la IDSymbol que vous avez créé précédemment. Cet attribut spécifie une liste délimitée par des virgules des icônes à utiliser dans le VSPackage. Icônes pas dans la liste sont exclus formulaire compilation.  
  
         Le bloc de Bitmap doit ressembler à ceci :  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Dans existants `<Button>` élément, définissez la `Icon` élément aux valeurs GUIDSymbol et IDSymbol vous avez créé précédemment. Voici un exemple d’un élément de bouton avec ces valeurs :  
  
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
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Schéma de référence XML VSCT](../extensibility/vsct-xml-schema-reference.md)
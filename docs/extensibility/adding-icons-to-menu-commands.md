---
title: "Ajouter des ic&#244;nes aux commandes de Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "icônes (Visual Studio), ajouter aux barres d’outils"
  - "barres d’outils (Visual Studio), ajouter des icônes aux commandes"
  - "commandes (Visual Studio), ajouter des icônes"
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Ajouter des ic&#244;nes aux commandes de Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les commandes peuvent apparaître dans les menus et barres d’outils. Barres d’outils, il est courant pour une commande à afficher avec une simple icône \(pour économiser de l’espace\) lors des menus qu'une commande apparaît généralement avec une icône et du texte.  
  
 Icônes 16 pixels de large par 16 pixels de haut et peuvent être une profondeur de couleurs de 8 bits \(256 couleurs\) ou de profondeur de couleur 32 bits \(couleurs\). icônes de couleur 32 bits sont préférables. Icônes sont généralement organisés dans une seule ligne horizontale dans une seule bitmap, même si plusieurs images sont autorisées. Cette image bitmap est déclarée dans le fichier .vsct avec chacune des icônes disponibles dans la bitmap. Consultez la référence pour le [Élément de bitmaps](../extensibility/bitmaps-element.md) Pour plus de détails.  
  
## Ajout d’une icône à une commande  
 La procédure suivante suppose que vous avez un projet VSPackage existant avec une commande de menu. Pour savoir comment procéder, consultez la page [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
1.  Créer un bitmap avec une profondeur de couleur de 32 bits. Une icône est toujours un multiple de 16 pixels de large et de 16 x 16 pour cette image bitmap doit être 16 pixels de haut.  
  
     Chaque icône est placée sur l’image bitmap à côté d’eux dans une seule ligne. Utilisez le canal alpha pour indiquer les emplacements de transparence de chaque icône.  
  
     Si vous utilisez une profondeur de couleur de 8 bits, utilisez magenta, `RGB(255,0,255)`, comme la transparence. Toutefois, les icônes de couleur 32 bits sont préférables.  
  
2.  Copiez le fichier icône dans le répertoire de ressources dans votre projet VSPackage. Dans l’Explorateur de solutions, ajoutez l’icône au projet. \(Sélectionner des ressources et dans le menu contextuel, cliquez sur Ajouter, puis sur un élément existant, sélectionnez votre fichier d’icône.\)  
  
3.  Ouvrez le fichier .vsct dans l’éditeur.  
  
4.  Ajouter un `GuidSymbol` élément avec un nom de **testIcon**. Créer un GUID \(**Outils \/ Créer GUID**, puis sélectionnez **Format du Registre** et cliquez sur Copier\) et collez\-la dans le `value` attribut. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
    ```  
  
5.  Ajouter un `<IDSymbol>` de l’icône. Le `name` attribut est l’ID de l’icône et la `value` indique sa position sur la bande, le cas échéant. S’il existe qu’une seule icône, ajoute 1. Le résultat doit ressembler à ceci :  
  
    ```xml  
    <!-- Create your own GUID -->  
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">  
        <IDSymbol name="testIcon1" value="1" />  
    </GuidSymbol>  
    ```  
  
6.  Créer un `<Bitmap>` dans la `<Bitmaps>` section du fichier .vsct pour représenter le bitmap contenant les icônes.  
  
    -   Définir le `guid` valeur au nom de la `<GuidSymbol>` élément que vous avez créé à l’étape précédente.  
  
    -   Définir le `href` valeur le chemin d’accès relatif du fichier bitmap \(dans ce cas **ressources\\ \< nom du fichier icône \>**.  
  
    -   Définir le `usedList` valeur à la IDSymbol que vous avez créé précédemment. Cet attribut spécifie une liste délimitée par des virgules des icônes à utiliser dans le VSPackage. Icônes pas dans la liste sont exclus formulaire compilation.  
  
         Le bloc de Bitmap doit ressembler à ceci :  
  
        ```xml  
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>  
        ```  
  
7.  Dans existant `<Button>` élément, définissez la `Icon` élément valeurs GUIDSymbol et IDSymbol vous avez créé précédemment. Voici un exemple d’un élément Button avec ces valeurs :  
  
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
  
## Voir aussi  
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Référence de schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md)
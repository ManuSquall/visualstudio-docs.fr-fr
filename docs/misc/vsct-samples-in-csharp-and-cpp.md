---
title: "Exemples VSCT en C# et C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT, exemples de fichiers"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# Exemples VSCT en C# et C++
VSCT est devenu la nouvelle façon de définir des commandes.  De ce fait, une modification s'est produite dans la façon dont les exemples de VSCT sont compilés en c\# et C\+\+.  Les commandes sont désormais définies en C\+\+ avec les fichiers externes et en c\# avec une section de symboles dans le fichier de .vsct.  
  
## définir des commandes  
  
### Fichiers externes C\+\+  
 Dans les exemples C\+\+, le compilateur de VSCT inclut les fichiers externes pour définir des constantes utilisées dans les définitions de vos commandes.  La méthode pour comprendre ces fichiers et définir de cette façon des constantes dans les définitions de vos commandes consiste à ajouter une balise d' `Extern` dans le fichier de .vsct et de spécifier le nom des références de fichiers externes à l'intérieur de l'attribut d' `href` .  ces fichiers sont :  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 L'extrait de code suivant du fichier c\+\+ .vsct indique comment inclure ces fichiers :  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### Symboles c\#  
 Dans les exemples c\#, le fichier de .vsct a une section d' `Symbols` dans le fichier lui\-même pour définir des commandes.  La définition des symboles dans un fichier de .vsct en c\# provient de la façon dont les ID des éléments sont définis par le comité de contrôle.  Voici un extrait de code à partir d'un fichier c\# .vsct qui spécifie les commandes et les constantes sont associées :  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## bitmap d'incorporation  
  
### C\#  
 Des bitmaps dans des fichiers binaires C\+\+ et c\# CTO sont stockées extérieurement sur le disque.  L'identificateur de bitmap est défini de telle sorte que la définition doit fournir un attribut du GUID pour la bitmap, un attribut d' `resID` de la bande de bitmap contenant les bitmaps, puis les identificateurs numériques des éléments utilisés à l'intérieur d'une définition de bouton \(attribut d'`usedList` \).  Un aspect important de cette déclaration est que l'identificateur d'élément doit être l'index réel \(base 1\) de l'intérieur de bitmap la bande de bitmap.  
  
 Dans l'exemple suivant il inclut une bande de bitmap qui contient uniquement un élément.  L'ID pour cet élément est défini comme guidMenuAndCommandsCmdSet : le bmpArrow, le bmpArrow doit être défini comme 1.  c'est également la déclaration de la bitmap.  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## Voir aussi  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
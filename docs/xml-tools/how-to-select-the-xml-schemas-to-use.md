---
title: "Proc&#233;dure&#160;: s&#233;lectionner les sch&#233;mas XML &#224; utiliser | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: s&#233;lectionner les sch&#233;mas XML &#224; utiliser
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'Éditeur XML fournit un cache de schéma dans le répertoire %InstallDir%\\Xml\\Schemas.Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.  
  
 La propriété de document **Schemas** permet de sélectionner un ou plusieurs schémas de langage XSD \(XML schema definition\) à utiliser.Elle permet de choisir des schémas dans le cache de schéma ou de spécifier un schéma situé ailleurs dans le cache.  
  
 Les schémas spécifiés sont enregistrés dans le fichier masqué d'options utilisateur de la solution \(.suo\), avec toutes les autres propriétés de document XML.Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.  
  
> [!NOTE]
>  L'éditeur peut effectuer la validation à l'aide d'un schéma inline ou d'un schéma dont la référence est fournie par l'attribut `xsd:schemaLocation`.Pour plus d'informations, consultez [Validation de documents XML](../xml-tools/xml-document-validation.md).  
  
### Pour sélectionner un schéma XML dans le cache de schéma  
  
1.  Ouvrez un fichier dans l'éditeur XML.  
  
2.  Dans la fenêtre de propriétés du document, cliquez sur le bouton du champ **Schémas**.  
  
     La boîte de dialogue **Schémas XML** s'affiche.La boîte de dialogue répertorie tous les schémas portant une extension .xsd dans le cache de schéma \(notamment les schémas désignés dans le fichier catalog.xml\) ainsi que tout schéma contenu dans la solution actuelle, ouvert dans Visual Studio, désigné par un attribut `xsd:schemaLocation` ou dans la propriété **Schemas**.  
  
3.  Sélectionnez les schémas à utiliser pour la validation en effectuant l'une des opérations suivantes :  
  
    -   Sélectionnez un schéma dans la boîte de dialogue **Schémas XML**, cliquez sur la colonne **Utiliser**, puis sélectionnez **Utiliser ce schéma**.  
  
     \-ou\-  
  
    -   Sélectionnez plusieurs schémas dans la boîte de dialogue **Schémas XML**, cliquez avec le bouton droit et sélectionnez **Utiliser ce schéma**.  
  
4.  Cliquez sur **OK**.  
  
     La liste des schémas sélectionnés est recopiée dans la propriété de document **Schemas**.  
  
### Pour ajouter un schéma XML au cache de schéma  
  
1.  Dans la fenêtre de propriétés du document, cliquez sur le bouton du champ **Schémas**.  
  
2.  Cliquez sur **Ajouter**.  
  
     La boîte de dialogue **Ouvrir le schéma XSD** s'affiche.  
  
3.  Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.  
  
4.  Cliquez sur **Ouvrir**.  
  
     Les schémas sont ajoutés au cache de schéma et la colonne **Utiliser** est définie sur **Utiliser ce schéma**.  
  
### Pour supprimer un schéma XML du cache de schéma  
  
1.  Dans la fenêtre de propriétés du document, cliquez sur le bouton du champ **Schémas**.  
  
2.  Sélectionnez le schéma à supprimer, puis cliquez sur **Supprimer**.  
  
     Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.  
  
    > [!NOTE]
    >  Si vous disposez toujours d'une référence au schéma via un attribut `schemaLocation` ou via un `targetNamespace` correspondant, l'action **Supprimer** ne fonctionnera pas dans ce cas en raison d'une association automatique.Il est alors recommandé de marquer le schéma avec la mention **Ne pas utiliser les schémas sélectionnés** de la colonne **Utiliser**.  
  
## Voir aussi  
 [Cache de schéma](../xml-tools/schema-cache.md)   
 [Boîte de dialogue Schémas XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Éditeur XML](../xml-tools/xml-editor.md)
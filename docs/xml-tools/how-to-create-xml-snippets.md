---
title: "Proc&#233;dure&#160;: cr&#233;er des extraits XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: cr&#233;er des extraits XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser l'éditeur XML pour créer de nouveaux extraits XML.Cet éditeur comporte un extrait XML appelé « Snippet », qui est souvent utilisé pour la création de nouveaux extraits XML.  
  
## Pour créer un nouvel extrait XML  
 Pour créer un nouvel extrait de code XML, créez un fichier XML et utilisez la fonction **Insérer un extrait**.  
  
1.  Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Fichier**.  
  
2.  Cliquez sur **Fichier XML**, puis sur **Ouvrir**.  
  
3.  Cliquez avec le bouton droit dans le volet de l'éditeur et sélectionnez **Insérer un extrait**.  
  
4.  Sélectionnez **Snippet** dans la liste et appuyez sur ENTRÉE.  
  
5.  Apportez les modifications voulues au nouvel extrait.  
  
6.  Dans le menu **Fichier**, sélectionnez **Enregistrer XMLFile.xml**.  
  
     La boîte de dialogue **Enregistrer le fichier sous** s'affiche.  
  
7.  Entrez le nom du nouvel extrait et sélectionnez **Fichiers d'extraits** dans la liste déroulante **Type de fichier**.  
  
8.  Utilisez la liste déroulante **Enregistrer dans** pour remplacer l'emplacement du fichier par Mes documents\\Visual Studio 2005\\Code Snippets\\XML\\My XML Snippets, puis cliquez sur **Enregistrer**.  
  
## Description des extraits  
 Cette section décrit certains éléments clés de l'extrait souvent utilisé.Pour plus d'informations sur les éléments de schéma utilisés par les extraits XML, consultez [Référence de schéma des extraits de code](../ide/code-snippets-schema-reference.md).  
  
### Élément SnippetType  
 L'éditeur prend en charge deux types d'extraits :  
  
```  
<SnippetTypes>  
  <SnippetType>SurroundsWith</SnippetType>  
  <SnippetType>Expansion</SnippetType>  
</SnippetTypes>  
```  
  
 Le type `Expansion` détermine si l'extrait apparaît lorsque vous appelez la commande **Insérer un extrait**.Le type `SurroundsWith` détermine si l'extrait apparaît lorsque vous appelez la commande **Entourer de**.  
  
### Élément Code  
 L'élément `Code` définit le texte XML qui sera inséré lorsque l'extrait sera appelé.  
  
> [!NOTE]
>  Le texte de l'extrait XML doit être placé dans une section `<![CDATA[...]]>`.  
  
 L'élément `Code` suivant est créé par l'extrait souvent utilisé.  
  
```  
<Code Language="XML">  
  <![CDATA[<test>  
  <name>$name$</name>  
  $selected$ $end$</test>]]>  
</Code>  
```  
  
 L'élément `Code` inclut trois variables.  
  
-   $name$ est une variable définie par l'utilisateur.Elle crée un élément `name` dont la valeur par défaut modifiable est « name ».Les variables définies par l'utilisateur se définissent à l'aide de l'élément `Literal`.  
  
-   $selected$ est une variable prédéfinie.Elle représente le texte sélectionné dans l'éditeur XML avant l'appel de l'extrait.La position de cette variable détermine l'emplacement du texte sélectionné dans l'extrait de code qui entoure cette sélection.  
  
-   $end$ est une variable prédéfinie.Lorsque l'utilisateur appuie sur ENTRÉE pour terminer l'édition des champs de l'extrait de code, cette variable détermine l'endroit où le signe ^ est placé.  
  
 L'élément `Code` ci\-dessus insère le texte XML suivant :  
  
```  
<test>  
  <name>name</name>  
</test>  
```  
  
 La valeur de l'élément name est marquée comme une zone modifiable.  
  
### Élément Literal  
 L'élément `Literal` permet d'identifier le texte de remplacement qui peut être personnalisé après son insertion dans le fichier.Par exemple, des chaînes littérales, des valeurs numériques et certains noms de variables peuvent être déclarés comme littéraux.Vous pouvez définir un nombre quelconque de littéraux dans votre extrait XML et y faire référence plusieurs fois dans l'extrait.L'exemple d'élément `Literal` suivant définit une variable $name$ dont la valeur par défaut est « name ».  
  
```  
<Literal>  
  <ID>name</ID>  
  <Default>name</Default>  
</Literal  
```  
  
 Les littéraux peuvent également faire référence à des fonctions.L'éditeur XML comprend une fonction intitulée **LookupPrefix**.Cette fonction  recherche l'URI d'espace de noms depuis l'emplacement du document XML où cet extrait est appelé et retourne le préfixe éventuel défini pour cet espace de noms, y compris le signe deux\-points \(:\) contenu dans ce nom.L'exemple d'élément `Literal` suivant utilise la fonction **LookupPrefix**.  
  
```  
<Literal Editable="false">  
   <ID>prefix</ID>  
   <Function>LookupPrefix("namespaceURI")</Function>  
</Literal>  
```  
  
 La variable $prefix$ \_peut alors être utilisée ailleurs dans votre extrait XML.  
  
## Voir aussi  
 [Extraits XML](../xml-tools/xml-snippets.md)   
 [Procédure : utiliser des extraits XML](../xml-tools/how-to-use-xml-snippets.md)   
 [Procédure : générer un extrait XML à partir d'un schéma XML](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)
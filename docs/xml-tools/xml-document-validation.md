---
title: "Validation de documents XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Validation de documents XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur XML vérifie la syntaxe XML 1.0 et effectue une validation des données en cours de frappe.L'éditeur peut effectuer cette validation à l'aide d'une définition de type de document \(DTD\) ou d'un schéma.Des soulignements ondulés rouges marquent les erreurs XML 1.0 correctement construites.Des soulignements ondulés bleus marquent les erreurs sémantiques d'après la validation de la DTD ou du schéma.La liste d'erreurs comporte une entrée pour chaque erreur détectée.Vous pouvez également afficher le message d'erreur en plaçant le curseur sur la ligne ondulée.  
  
 Les schémas utilisés pour la validation sont recherchés en fonction de la comparaison du `targetNamespace` d'un schéma compilé à la déclaration xmlns de l'élément.Les schémas compilés sont chargés à partir d'un des emplacements suivants, répertoriés par ordre de priorité :  
  
-   Nom de fichier spécifié dans le champ **Schémas** de la fenêtre Propriétés du document  
  
-   Une DTD ou un schéma inline  
  
-   Une DTD externe ou un attribut `xsd:schemaLocation` et `xsd:noNamespaceSchemaLocation`  
  
-   Un URI d'espace de noms de schéma XDR « x\-schema »  
  
 Des schémas peuvent également être recherchés dans les emplacements supplémentaires suivants lorsque le schéma contient un espace de noms cible non vide :  
  
-   Une autre fenêtre d'éditeur qui contient le schéma  
  
-   Un schéma contenu dans la solution actuelle  
  
-   Un schéma du répertoire de cache de schéma  
  
## Fichiers XSLT  
 Lorsque vous modifiez un fichier XSLT, le fichier xslt.xsd situé du cache de schéma est utilisé pour la validation.Les erreurs de validation sont indiquées par des soulignements ondulés bleus.Les erreurs provenant du compilateur XSLT sont signalées par des soulignements ondulés rouges.  
  
## Fichiers XSD \(XML schema definition\)  
 Lorsque vous modifiez un fichier de schéma XML, le fichier xsdschema.xsd situé dans le cache de schéma est utilisé pour la validation.Les erreurs de validation sont indiquées par des soulignements ondulés bleus.Les erreurs de compilation sont signalées de la même façon.  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)
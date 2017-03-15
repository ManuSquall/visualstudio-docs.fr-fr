---
title: "Proc&#233;dure&#160;: cr&#233;er un sch&#233;ma XML &#224; partir d&#39;un document XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Proc&#233;dure&#160;: cr&#233;er un sch&#233;ma XML &#224; partir d&#39;un document XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'éditeur XML permet de créer un schéma de langage XSD \(XML Schema definition\) à partir d'un document XML.Le document d'instance XML détermine la façon dont le schéma est généré, comme suit :  
  
-   Si le document XML n'a pas de schéma ni de DTD \(définition de type de document\) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.  
  
-   Si le document XML a une DTD associée, la DTD externe et le sous\-ensemble interne sont convertis en un schéma XML correspondant.  
  
-   Si le document XML comporte un schéma XDR \(XML\-Data Reduced\) intégré, le schéma XDR est converti en un schéma XML correspondant.  
  
 Les schémas créés sont ensuite utilisés pour fournir une fonctionnalité IntelliSense pour le document XML.  
  
 Pour plus d'informations sur le moteur d'inférence de schéma, consultez [Inférence d'un schéma XML](../Topic/Inferring%20an%20XML%20Schema.md).  
  
### Pour créer un schéma XML  
  
1.  Chargez un document d'instance XML dans l'éditeur XML.  
  
2.  Cliquez sur le bouton **Créer un schéma** dans la **Barre d'outils**.  
  
     Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le document d'instance XML.Chaque schéma est ouvert comme un fichier divers temporaire.  
  
     Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.  
  
    > [!NOTE]
    >  La commande **Créer un schéma** est également disponible dans le menu contextuel de l'éditeur XML et dans le menu **XML**.  
  
## Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)
---
title: "Comment : créer un schéma XML à partir d’un Document XML | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 811107d3eb5c2c9c974b3d01041bcc9d1bdcbbc9
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procédure : créer un schéma XML à partir d'un document XML
L'éditeur XML permet de créer un schéma de langage XSD (XML Schema definition) à partir d'un document XML. Le document d'instance XML détermine la façon dont le schéma est généré, comme suit :  
  
-   Si le document XML n'a pas de schéma ni de DTD (définition de type de document) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.  
  
-   Si le document XML a une DTD associée, la DTD externe et le sous-ensemble interne sont convertis en un schéma XML correspondant.  
  
-   Si le document XML comporte un schéma XDR (XML-Data Reduced) intégré, le schéma XDR est converti en un schéma XML correspondant.  
  
Les schémas créés sont ensuite utilisés pour fournir une fonctionnalité IntelliSense pour le document XML.  
  
Pour plus d’informations sur le moteur d’inférence de schéma, consultez [déduire un schéma XML](/dotnet/standard/data/xml/inferring-an-xml-schema).  
  
### <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML  
  
1.  Chargez un document d'instance XML dans l'éditeur XML.  
  
2.  Cliquez sur le **Create Schema** bouton à partir de la **barre d’outils**.  
  
     Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le document d'instance XML. Chaque schéma est ouvert comme un fichier divers temporaire.  
  
     Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.  
  
    > [!NOTE]
    >  Le **Create Schema** commande est également disponible dans le menu contextuel de l’éditeur XML et, sous la **XML** menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)
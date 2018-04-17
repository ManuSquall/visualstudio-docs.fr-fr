---
title: 'Comment : créer un schéma XML à partir d’un Document XML | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b19421bf9cb9d974a837f557d8b75ac4d5ba89c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
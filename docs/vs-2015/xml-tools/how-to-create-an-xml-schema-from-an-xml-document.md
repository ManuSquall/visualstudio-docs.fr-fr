---
title: 'Comment : créer un schéma XML à partir d’un Document XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5d2e4cc78ee79502c4f2e10b2343fa0723006b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181264"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procédure : créer un schéma XML à partir d'un document XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
L'éditeur XML permet de créer un schéma de langage XSD (XML Schema definition) à partir d'un document XML. Le document d'instance XML détermine la façon dont le schéma est généré, comme suit :  
  
-   Si le document XML n'a pas de schéma ni de DTD (définition de type de document) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.  
  
-   Si le document XML a une DTD associée, la DTD externe et le sous-ensemble interne sont convertis en un schéma XML correspondant.  
  
-   Si le document XML comporte un schéma XDR (XML-Data Reduced) intégré, le schéma XDR est converti en un schéma XML correspondant.  
  
 Les schémas créés sont ensuite utilisés pour fournir une fonctionnalité IntelliSense pour le document XML.  
  
 Pour plus d’informations sur le moteur d’inférence de schéma, consultez [inférence d’un schéma XML](http://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML  
  
1.  Chargez un document d'instance XML dans l'éditeur XML.  
  
2.  Cliquez sur le **Create Schema** bouton à partir de la **barre d’outils**.  
  
     Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le document d'instance XML. Chaque schéma est ouvert comme un fichier divers temporaire.  
  
     Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.  
  
    > [!NOTE]
    >  Le **Create Schema** commande est également disponible dans le menu contextuel de l’éditeur XML et, sous la **XML** menu.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)




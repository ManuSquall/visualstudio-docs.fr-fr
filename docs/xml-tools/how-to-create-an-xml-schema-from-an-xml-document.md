---
title: "Procédure : création d'un schéma XML à partir d'un document XML"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebea3b20bc606ec82529e4a9b2a547d6a44fc905
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953787"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procédure : Créer un schéma XML à partir d’un document XML

L'éditeur XML permet de créer un schéma de langage XSD (XML Schema definition) à partir d'un document XML. Le document d'instance XML détermine la façon dont le schéma est généré, comme suit :

-   Si le document XML n'a pas de schéma ni de DTD (définition de type de document) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.

-   Si le document XML a une DTD associée, la DTD externe et le sous-ensemble interne sont convertis en un schéma XML correspondant.

-   Si le document XML comporte un schéma XDR (XML-Data Reduced) intégré, le schéma XDR est converti en un schéma XML correspondant.

Les schémas créés sont ensuite utilisés pour fournir une fonctionnalité IntelliSense pour le document XML.

Pour plus d’informations sur le moteur d’inférence de schéma, consultez [inférence d’un schéma XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML

1.  Chargez un document d'instance XML dans l'éditeur XML.

2.  Cliquez sur le **Create Schema** bouton à partir de la **barre d’outils**.

     Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le document d'instance XML. Chaque schéma est ouvert comme un fichier divers temporaire.

     Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.

    > [!NOTE]
    >  Le **Create Schema** commande est également disponible dans le menu contextuel de l’éditeur XML et, sous la **XML** menu.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
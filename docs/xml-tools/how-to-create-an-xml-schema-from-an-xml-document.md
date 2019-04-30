---
title: Créer un schéma XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783491"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procédure : Créer un schéma XML à partir d’un document XML

L’éditeur XML vous permet de créer un schéma de langage (XSD XML) de définition de schéma XML à partir d’un document XML. Le fichier XML détermine la façon dont la génération du schéma de la manière suivante :

- Si le document XML n'a pas de schéma ni de DTD (définition de type de document) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.

- Si le document XML a une DTD associée, la DTD externe et le sous-ensemble interne sont convertis en un schéma XML correspondant.

- Si le document XML comporte un schéma XDR (XML-Data Reduced) intégré, le schéma XDR est converti en un schéma XML correspondant.

Les schémas créés sont ensuite utilisés pour fournir IntelliSense pour le fichier XML.

Pour plus d’informations sur le moteur d’inférence de schéma, consultez [déduire un schéma XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML

1. Ouvrez un fichier XML dans Visual Studio.

2. Dans la barre de menus, choisissez **XML** > **Create Schema**.

   Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le fichier XML. Chaque schéma est ouvert comme un fichier divers temporaire. Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)
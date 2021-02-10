---
title: Créer un schéma XML
description: Découvrez comment utiliser l’éditeur XML dans Visual Studio pour créer un schéma en langage XSD (XML Schema Definition) à partir d’un document XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970281"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Procédure : créer un schéma XML à partir d’un document XML

L’éditeur XML vous permet de créer un schéma en langage XSD (XML Schema Definition) à partir d’un document XML. Le fichier XML détermine la façon dont le schéma est généré de la manière suivante :

- Si le document XML n'a pas de schéma ni de DTD (définition de type de document) associée, les données du document XML sont utilisées pour inférer un nouveau schéma XML.

- Si le document XML a une DTD associée, la DTD externe et le sous-ensemble interne sont convertis en un schéma XML correspondant.

- Si le document XML comporte un schéma XDR (XML-Data Reduced) intégré, le schéma XDR est converti en un schéma XML correspondant.

Les schémas créés sont ensuite utilisés pour fournir IntelliSense pour le fichier XML.

Pour plus d’informations sur le moteur d’inférence de schéma, consultez [déduire un schéma XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Pour créer un schéma XML

1. Ouvrez un fichier XML dans Visual Studio.

2. Dans la barre de menus, choisissez **XML**  >  **créer un schéma**.

   Un document de schéma XML est créé et ouvert pour chaque espace de noms trouvé dans le fichier XML. Chaque schéma est ouvert comme un fichier divers temporaire. Les schémas peuvent être enregistrés sur disque, ajoutés à votre projet ou ignorés.

## <a name="see-also"></a>Voir aussi

- [Éditeur XML](../xml-tools/xml-editor.md)

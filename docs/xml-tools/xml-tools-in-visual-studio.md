---
title: Éditeur de schéma et éditeur XML
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e763fa3475f26b9742ea5fb7061978e711eb22ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816421"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Vue d’ensemble des outils XML dans Visual Studio

*Extensible Markup Language (XML)* est un langage de balisage qui fournit un format pour la description des données. XML sépare les données et leur présentation à l’aide de feuilles de style associées telles que le langage XSL (Extensible Stylesheet Language) et les feuilles de style en cascade (CSS). Visual Studio comprend des outils et des fonctions qui facilitent l'utilisation de XML, de XSLT et des schémas XML.

## <a name="xml-editor"></a>Éditeur XML

L' [éditeur XML](xml-editor.md) permet de modifier des documents XML. Il fournit la vérification de la syntaxe XML complète, la validation de schéma pendant que vous tapez, le codage en couleurs et IntelliSense. Si un schéma ou une définition de type de document est fournie, IntelliSense l'utilise pour répertorier les éléments et attributs possibles.

Les fonctionnalités supplémentaires sont les suivantes :

- Prise en charge des extraits XML, y compris les extraits générés par schéma

- Mode plan du document afin que les éléments puissent être développés et réduits

- La possibilité d’exécuter des transformations XSLT et d’afficher les résultats sous forme de texte, XML ou HTML

- Possibilité de générer des schémas en langage XSD (XML Schema Definition) à partir du document d’instance XML

- Prise en charge de la modification des feuilles de style XSLT, y compris la prise en charge IntelliSense

- Explorateur de schémas XML

## <a name="xml-schema-designer"></a>Concepteur de schémas XML

Le [Concepteur de schémas XML](xml-schema-designer.md) est intégré à Visual Studio et à l’éditeur XML pour vous permettre de travailler avec des schémas en langage XSD (XML Schema Definition).

## <a name="xslt-debugging"></a>Débogage XSLT

Visual Studio prend en charge le [débogage des feuilles de style XSLT](../xml-tools/debugging-xslt.md). Le débogueur permet de définir des points d'arrêt dans une feuille de style XSLT, d'exécuter pas à pas la feuille de style XSLT à partir du code, etc.

> [!NOTE]
> Le débogueur XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml?displayProperty=fullName>
- [Transformations XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Traiter des données XML à l’aide du modèle de données XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [DOM (Document Object Model) XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Modèle Objet du schéma (SOM) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)

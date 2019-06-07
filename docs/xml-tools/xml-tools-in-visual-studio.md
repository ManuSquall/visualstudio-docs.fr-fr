---
title: Éditeur XML et le Concepteur de schémas
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7493d6c10c83b16ad7579299a49a7747e34c20b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746519"
---
# <a name="xml-tools-in-visual-studio"></a>Outils XML dans Visual Studio

*Langage XML (Extensible Markup)* est un langage de balisage qui fournit un format de description des données. Le langage XML sépare les données et sa présentation à l’aide associée à des feuilles de style comme langage XSL (Extensible Stylesheet) et les feuilles de style en cascade (CSS). Visual Studio comprend des outils et des fonctions qui facilitent l'utilisation de XML, de XSLT et des schémas XML.

## <a name="xml-editor"></a>Éditeur XML

Le [éditeur XML](xml-editor.md) sert à modifier des documents XML. Il fournit la syntaxe XML complète, la vérification, la validation de schéma lors de la frappe, codage en couleurs et IntelliSense. Si un schéma ou une définition de type de document est fournie, IntelliSense l'utilise pour répertorier les éléments et attributs possibles.

Autres fonctionnalités de l’éditeur :

- Prise en charge XML extrait de code, notamment des extraits générés par schéma

- Plan, ce qui peuvent être développés et réduire les éléments de document

- La possibilité d’exécuter des transformations XSLT et d’afficher les résultats en tant que texte, XML ou HTML

- La capacité à générer des schémas XML Schema definition language (XSD) à partir du document d’instance XML

- Prise en charge pour la modification des feuilles de style XSLT, y compris la prise en charge IntelliSense

- Explorateur de schémas XML

## <a name="xml-schema-designer"></a>Concepteur de schémas XML

Le [Concepteur de schémas XML](xml-schema-designer.md) est intégré à Visual Studio et l’éditeur XML pour vous permettre de travailler avec des schémas de langage (XSD XML) XML schema definition.

## <a name="xslt-debugging"></a>Débogage XSLT

Visual Studio prend en charge [le débogage de feuilles de style XSLT](../xml-tools/debugging-xslt.md). Le débogueur permet de définir des points d'arrêt dans une feuille de style XSLT, d'exécuter pas à pas la feuille de style XSLT à partir du code, etc.

> [!NOTE]
> Le débogueur XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml?displayProperty=fullName>
- [Transformations XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Traitement des données XML à l’aide du modèle de données XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [DOM (Document Object Model) XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Modèle Objet du schéma (SOM) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)
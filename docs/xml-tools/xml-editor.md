---
title: Éditeur XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2111286afde9e60391f1a7410fec2778b3ed673
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693784"
---
# <a name="xml-editor"></a>Éditeur XML

L’éditeur XML est basé sur l’éditeur de texte Visual Studio et inclut la prise en charge des langages XML. L’éditeur XML comprend les fonctionnalités suivantes :

- Vérification de la syntaxe XML 1.0

- Validation de schéma en cours de frappe

- Prise en charge des extraits XML, notamment des extraits générés par schéma

- Prise en charge des DTD (définition de type de document)

- Prise en charge des schémas de langage XSD (XML Schema definition)

- Création d'un schéma XML à partir d'un document d'instance XML

- Conversion d'une DTD ou d'un schéma XDR (XML-Data Reduced) en un schéma XML

- Vérification de la syntaxe XSLT 1.0

- Mise en plan des documents permettant de développer et réduire les éléments

- Intégration avec le [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md). Cela fournit une vue hiérarchique des schémas XML.

L’éditeur XML est appelée pour les extensions de fichier connues, telles que *.xml*, *.xsd*, *.xsl*, et *.config*. Il est également appelé à l’ouverture d’un fichier dont l’extension est inconnue mais qui contient du XML. Vous pouvez également ouvrir un fichier avec l’éditeur XML à l’aide de la **ouvrir avec** option et en sélectionnant l’éditeur XML dans la liste.

## <a name="xslt-intellisense"></a>IntelliSense XSLT

[IntelliSense XSLT](../xml-tools/xml-editor-intellisense-features.md) vous permet de compléter automatiquement l’attribut jeu de noms, les modes de modèle et les noms et les noms de paramètre pour un mode spécifié ou un modèle nommé.

## <a name="xslt-profiler"></a>Générateur de profils XSLT

Le [Générateur de profils XSLT](../xml-tools/walkthrough-xslt-profiler.md) crée des performances XSLT détaillés des rapports qui vous aident à mesurent, évaluent et ciblent les problèmes de performances dans le code XSLT. Le Générateur de profils XSLT inclut également des conseils utiles pour les optimisations de feuille de style XSL et XSLT.

## <a name="xslt-hierarchy"></a>Hiérarchie XSLT

Le [outil de la hiérarchie XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md) vous permet d’ajouter des points d’arrêt dans les feuilles de style incluses et/ou les règles de modèle intégrées.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md) fournit des informations sur l’éditeur de texte.
- [Référence du standard XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) fournit des informations sur les technologies XML, notamment XML, définition de Type de Document (DTD), le langage de définition de schéma XML (XSD) et XSLT.
- [Outils XML dans Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
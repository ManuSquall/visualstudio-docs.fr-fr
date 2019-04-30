---
title: 'CA3077 : Traitement non sécurisé dans la conception d’API, le document XML et le lecteur de texte XML'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd3b17ad3449bebcab57344355f7cc7687ea6b19
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541075"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077 : Traitement non sécurisé dans la conception d’API, le document XML et le lecteur de texte XML

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Lors de la conception d’une API dérivée de XMLDocument et XMLTextReader, tenez compte de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  L’utilisation d’instances de DTDProcessing non sécurisées lors de la référence ou la résolution de sources d’entités externes ou la définition de valeurs non sécurisées dans le code XML peut aboutir à la divulgation d’informations.

## <a name="rule-description"></a>Description de la règle
 Une *définition de type de document (DTD)* est l’une des deux façons pour un analyseur XML de déterminer la validité d’un document, comme défini par la recommandation du  [World Wide Web Consortium (W3C) sur le langage XML (Extensible Markup Language) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Cette règle recherche les propriétés et instances où les données non fiables sont acceptées pour informer les développeurs de menaces de [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) éventuelles, qui peuvent entraîner des attaques [par déni de service](/dotnet/framework/wcf/feature-details/denial-of-service) . Cette règle se déclenche quand :

- <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlTextReader> classes utilisent les valeurs du programme de résolution par défaut pour le traitement des DTD.

- Aucun constructeur n’est défini pour les classes dérivées XmlDocument ou XmlTextReader, ou aucune valeur sécurisée n’est utilisée pour <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Intercepter et traiter toutes les exceptions XmlTextReader correctement pour éviter la divulgation d’informations de chemin d’accès.

- Utilisez <xref:System.Xml.XmlSecureResolver>au lieu de XmlResolver pour limiter les ressources XmlTextReader peut accéder.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Sauf si vous êtes sûr que l’entrée provient d’une source fiable, ne supprimez aucune règle de cet avertissement.

## <a name="pseudo-code-examples"></a>Exemples de pseudo-code

### <a name="violation"></a>Violation

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```
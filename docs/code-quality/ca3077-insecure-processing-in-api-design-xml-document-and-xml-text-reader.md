---
title: "CA3077&#160;: traitement non s&#233;curis&#233; dans la conception d’API, le document XML et le lecteur de texte XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077&#160;: traitement non s&#233;curis&#233; dans la conception d’API, le document XML et le lecteur de texte XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## Cause  
 Lors de la conception d’une API dérivée de XMLDocument et XMLTextReader, tenez compte de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  L’utilisation d’instances de DTDProcessing non sécurisées lors de la référence ou la résolution de sources d’entités externes ou la définition de valeurs non sécurisées dans le code XML peut aboutir à la divulgation d’informations.  
  
## Description de la règle  
 Une [définition de type de document \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) est l’une des deux façons pour un analyseur XML de déterminer la validité d’un document, comme défini par la recommandation du [World Wide Web Consortium \(W3C\) sur le langage XML \(Extensible Markup Language\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Cette règle recherche les propriétés et instances où les données non fiables sont acceptées pour informer les développeurs de menaces de [Divulgation d'informations](../Topic/Information%20Disclosure.md) éventuelles, qui peuvent entraîner des attaques [par déni de service](../Topic/Denial%20of%20Service.md). Cette règle se déclenche quand :  
  
-   Les classes <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlTextReader> utilisent les valeurs du programme de résolution par défaut pour le traitement DTD.  
  
-   Aucun constructeur n’est défini pour les classes dérivées XmlDocument ou XmlTextReader, ou aucune valeur sécurisée n’est utilisée pour <xref:System.Xml.XmlResolver>.  
  
## Comment corriger les violations  
  
-   Interceptez et traitez toutes les exceptions XmlTextReader  correctement pour éviter la divulgation d’informations relatives au chemin.  
  
-   Utilisez <xref:System.Xml.XmlSecureResolver> au lieu de XmlResolver pour limiter les ressources auxquelles  XmlTextReader  peut accéder.  
  
## Quand supprimer les avertissements  
 Sauf si vous êtes sûr que l’entrée provient d’une source fiable, ne supprimez aucune règle de cet avertissement.  
  
## Exemples de pseudo\-code  
  
### Violation  
  
```c#  
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
  
### Solution  
  
```c#  
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
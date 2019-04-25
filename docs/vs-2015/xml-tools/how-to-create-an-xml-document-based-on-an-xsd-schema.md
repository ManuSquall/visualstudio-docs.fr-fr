---
title: 'Procédure : Créer un Document XML basé sur un schéma XSD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 623da37807e0fd61041bfeb9ab411ce0cb96d4b5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091121"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procédure : Créer un document XML basé sur un schéma XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le **générer un exemple de code XML** fonctionnalité génère un exemple de fichier XML en fonction de votre fichier de schéma XSD (XML).  
  
 Vous pouvez utiliser cette option dans les scénarios suivants :  
  
- Comprendre l'utilisation des diverses constructions dans votre schéma.  
  
- confirmer la finalité du schéma.  
  
  Le **générer un exemple de code XML** fonctionnalité est disponible uniquement sur les éléments globaux et nécessite un jeu de schémas XML valid.  
  
  En règle générale, cette fonctionnalité permet de générer des documents XML valides. Toutefois, si le schéma contient un ou plusieurs des éléments suivants, l'exemple risque de ne pas être valide :  
  
- Contraintes d'identité `xs:key`, `xs:keyref` et `xs:unique`.  
  
- Facettes `xs:pattern`.  
  
- Énumérations du type `xs:QName`.  
  
- Types `xs:ENTITY`, `xs:ENTITIES` et `xs:NOTATION`.  
  
  Notez également que le contenu `xs:base64Binary` n'est généré que si des énumérations figurent dans le schéma du type correspondant.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Pour générer un document d'instance XML basé sur le fichier XSD  
  
1. Suivez les étapes de [Comment : Créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Dans le [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md), avec le bouton droit le `PurchaseOrder` élément global. Sélectionnez **générer l’exemple de code XML**.  
  
     Lorsque vous sélectionnez cette option, le fichier PurchaseOrder.xml avec l'exemple de contenu XML suivant est généré et ouvert dans l'Éditeur XML :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">  
      <ShipTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </ShipTo>  
      <ShipTo country="US">  
        <name>name2</name>  
        <street>street2</street>  
        <city>city2</city>  
        <state>state2</state>  
        <zip>-79228162514264337593543950335</zip>  
      </ShipTo>  
      <BillTo country="US">  
        <name>name1</name>  
        <street>street1</street>  
        <city>city1</city>  
        <state>state1</state>  
        <zip>1</zip>  
      </BillTo>  
    </PurchaseOrder>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de données XML](../xml-tools/working-with-xml-data.md)

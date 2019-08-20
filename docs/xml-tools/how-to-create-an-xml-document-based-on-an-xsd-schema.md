---
title: 'Procédure : Créer un document XML basé sur un schéma XSD'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7739f33bad62667fdc7be8704237ebdd3932739c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918562"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procédure : Créer un document XML basé sur un schéma XSD

La fonctionnalité **générer un exemple XML** génère un exemple de fichier XML basé sur votre fichier de schéma XML (XSD).

Vous pouvez utiliser cette option dans les scénarios suivants :

- Comprendre l'utilisation des diverses constructions dans votre schéma.

- confirmer la finalité du schéma.

La fonctionnalité **générer un exemple XML** est disponible uniquement sur les éléments globaux et requiert un jeu de schémas XML valide.

En règle générale, cette fonctionnalité permet de générer des documents XML valides. Toutefois, si le schéma contient un ou plusieurs des éléments suivants, l'exemple risque de ne pas être valide :

- Contraintes d'identité `xs:key`, `xs:keyref` et `xs:unique`.

- Facettes `xs:pattern`.

- Énumérations du type `xs:QName`.

- Types `xs:ENTITY`, `xs:ENTITIES` et `xs:NOTATION`.

Notez également que le contenu `xs:base64Binary` n'est généré que si des énumérations figurent dans le schéma du type correspondant.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Pour générer un document d'instance XML basé sur le fichier XSD

1. Suivez les étapes de [la procédure: Créez et modifiez un fichier](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)de schéma XSD.

2. Dans l' [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md), cliquez avec le `PurchaseOrder` bouton droit sur l’élément global. Sélectionnez **générer un exemple de code XML**.

     Lorsque vous sélectionnez cette option, PurchaseOrder. le fichier *XML* avec l’exemple de contenu XML suivant sera généré et ouvert dans l’éditeur XML:

    ```xml
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
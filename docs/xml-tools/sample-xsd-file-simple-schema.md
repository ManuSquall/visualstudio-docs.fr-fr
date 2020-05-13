---
title: 'Exemple de fichier XSD : schéma simple'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 788de9f31a58561aa743d6ca6286ef650f4297a4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75592540"
---
# <a name="sample-xsd-file-simple-schema"></a>Exemple de fichier XSD : schéma simple

Le fichier XSD suivant est utilisé dans différents exemples de la documentation du Concepteur de schémas XSD. Ce fichier est un schéma de bon de commande simple.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Les noms de sociétés, d'organisations, de produits, de domaines, d'adresses de messagerie, de logos, de personnes, de lieux et d'événements mentionnés dans les exemples sont fictifs. Toute ressemblance avec des noms, des logos, des personnes, des lieux ou des événements réels est purement fortuite et involontaire.

---
title: 'Procédure : Utiliser le Concepteur de schémas XML avec des littéraux XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1483077142d1c60d3309458aedbe1abd7e2e2b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863392"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procédure : Utiliser le Concepteur de schémas XML avec des littéraux XML

Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Pour créer un projet d'application console Visual Basic

1.  Démarrez Visual Studio.

2.  À partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**. La boîte de dialogue **Nouveau projet** s’affiche. Pour **types de projets**, sélectionnez **autres langages,** , puis sélectionnez **Visual Basic**. Pour **modèles**, sélectionnez Application Console. Puis tapez `XMLLiterals` dans le **nom** champ et un emplacement de projet dans le **emplacement** champ. Cliquez sur **OK**.

     Le nouveau projet est créé. Le projet XMLLiterals contient un fichier source Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Pour ajouter un fichier XSD existant au projet

1.  Ouvrez un nouveau fichier texte dans le bloc-notes. Copiez le code d’exemple de schéma XML à partir de [schéma d’ordre d’achat](../xml-tools/sample-xsd-file-simple-schema.md) et collez-le dans le fichier.

2.  Enregistrez le fichier dans un emplacement avec le nom *PurchaseOrderSchema.xsd*.

3.  Dans **l’Explorateur de solutions**, cliquez sur le nom du projet, sélectionnez **ajouter**, puis sélectionnez **élément existant**. Le **ajouter un élément existant** boîte de dialogue s’affiche. Accédez à la *PurchaseOrderSchema.xsd* fichier, sélectionnez-le, puis cliquez sur **ajouter**.

     Le projet XMLLiterals contient désormais deux fichiers : *Module1.vb* et *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Pour ajouter le code Visual Basic avec un littéral XML, selon le fichier XSD inclus dans le projet

1. Remplacez le code dans *Module1.vb* fichier par le code suivant :

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Avec le bouton droit n’importe quel nœud XML dans un littéral XML ou une importation d’espace de noms XML et sélectionnez **afficher dans l’Explorateur de schémas**.

    Le **Explorateur de schémas XML** est affiché côte à côte avec un fichier Visual Basic qui a le littéral XML associé au jeu de schémas XML.
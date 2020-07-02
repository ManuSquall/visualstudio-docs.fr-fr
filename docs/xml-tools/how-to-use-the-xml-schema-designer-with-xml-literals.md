---
title: 'Procédure : utiliser le Concepteur de schémas XML avec des littéraux XML'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b515092087ab213db5d3002f00c56753c2e3de14
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814640"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Comment : utiliser le concepteur de schémas XML avec des littéraux XML

Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Créer un projet de Visual Basic

1. Ouvrez Visual Studio.

2. Créez un nouveau Visual Basic projet d' **application console** nommé **XMLLiterals**.

     Le nouveau projet contient un Visual Basic fichier source *Module1. vb*.

## <a name="add-an-existing-xsd-file"></a>Ajouter un fichier XSD existant

1. Ouvrez un nouveau fichier texte dans le bloc-notes. Copiez l’exemple de code de schéma XML à partir du [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md) et collez-le dans le fichier.

2. Enregistrez le fichier à un emplacement portant le nom *PurchaseOrderSchema. xsd*.

3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, sélectionnez **Ajouter**, puis **élément existant**. La boîte de dialogue **élément AddExisting** s’affiche. Accédez au fichier *PurchaseOrderSchema. xsd* , sélectionnez-le, puis cliquez sur **Ajouter**.

     Le projet XMLLiterals contient maintenant deux fichiers : *Module1. vb* et *PurchaseOrderSchema. xsd*.

## <a name="add-code"></a>Ajout de code

Pour ajouter Visual Basic Code avec un littéral XML, en fonction du fichier XSD inclus dans le projet :

1. Remplacez le code du fichier *Module1. vb* par le code suivant :

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

2. Cliquez avec le bouton droit sur un nœud XML dans un littéral XML ou une importation d’espace de noms XML, puis sélectionnez **afficher dans l’Explorateur de schémas**.

   L' **Explorateur de schémas XML** s’affiche côte à côte avec un fichier Visual Basic contenant le littéral XML associé au jeu de schémas XML.

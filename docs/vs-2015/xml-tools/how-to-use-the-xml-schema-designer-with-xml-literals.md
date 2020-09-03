---
title: 'Comment : utiliser le concepteur de schémas XML avec des littéraux XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656293"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procédure : utiliser le Concepteur de schémas XML avec des littéraux XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Pour créer un projet d'application console Visual Basic

1. Démarrez Visual Studio 2010.

2. Dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**. La boîte de dialogue **Nouveau projet** apparaît. Pour **types de projets**, sélectionnez **autres langues,** puis **Visual Basic**. Pour **modèles**, sélectionnez application console. Ensuite, tapez dans le champ `XMLLiterals` **nom** et un emplacement de projet dans le champ **emplacement** . Cliquez sur **OK**.

     Le nouveau projet est créé. Le projet XMLLiterals contient un fichier source Visual Basic, Module1.vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Pour ajouter un fichier XSD existant au projet

1. Ouvrez un nouveau fichier texte dans le bloc-notes. Copiez l’exemple de code de schéma XML à partir du [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md) et collez-le dans le fichier.

2. Enregistrez le fichier à l'emplacement de votre choix avec le nom PurchaseOrderSchema.xsd.

3. Dans le Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, sélectionnez **Ajouter**, puis sélectionnez **élément existant...**. La boîte de dialogue **élément AddExisting** s’affiche. Accédez au fichier PurchaseOrderSchema. xsd, sélectionnez-le, puis cliquez sur **Ajouter**.

     Le projet XMLLiterals contient désormais deux fichiers : Module1.vb et PurchaseOrderSchema.xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Pour ajouter le code Visual Basic avec un littéral XML, selon le fichier XSD inclus dans le projet

1. Remplacez le code du fichier Module1.vb par le code suivant :

    ```
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

     L'Explorateur de schémas XML est affiché côte à côte avec un fichier Visual Basic dont le littéral XML est associé au jeu de schémas XML.

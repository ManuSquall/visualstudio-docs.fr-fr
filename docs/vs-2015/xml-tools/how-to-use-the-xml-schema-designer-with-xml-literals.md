---
title: 'Procédure : Utiliser le Concepteur de schémas XML avec des littéraux XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 05c32bfc6c3220739c433ef519b696953bc8b1b4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074945"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procédure : Utiliser le Concepteur de schémas XML avec des littéraux XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Pour créer un projet d'application console Visual Basic  
  
1. Démarrez Visual Studio 2010.  
  
2. À partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**. La boîte de dialogue **Nouveau projet** s’affiche. Pour **types de projets**, sélectionnez **autres langages,** , puis sélectionnez **Visual Basic**. Pour **modèles**, sélectionnez Application Console. Puis tapez `XMLLiterals` dans le **nom** champ et un emplacement de projet dans le **emplacement** champ. Cliquez sur **OK**.  
  
     Le nouveau projet est créé. Le projet XMLLiterals contient un fichier source Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Pour ajouter un fichier XSD existant au projet  
  
1. Ouvrez un nouveau texte de fichiers dans Notepad.Copy le code d’exemple de schéma XML à partir de [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md) et collez-le dans le fichier.  
  
2. Enregistrez le fichier à l'emplacement de votre choix avec le nom PurchaseOrderSchema.xsd.  
  
3. Dans l’Explorateur de solutions, cliquez sur le nom du projet, sélectionnez **ajouter**, puis sélectionnez **un élément existant...** . Le **ajouter un élément existant** boîte de dialogue s’affiche. Accédez au fichier PurchaseOrderSchema.xsd, sélectionnez-le, puis cliquez sur **ajouter**.  
  
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
  
2. Avec le bouton droit n’importe quel nœud XML dans un littéral XML ou une importation d’espace de noms XML et sélectionnez **afficher dans l’Explorateur de schémas**.  
  
     L'Explorateur de schémas XML est affiché côte à côte avec un fichier Visual Basic dont le littéral XML est associé au jeu de schémas XML.

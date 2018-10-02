---
title: 'Comment : utiliser le Concepteur de schémas XML avec des littéraux XML | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb0ba92afd8a3c8ab915d72237a5251643b32669
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500981"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procédure : utiliser le Concepteur de schémas XML avec des littéraux XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : utiliser le Concepteur de schémas XML avec des littéraux XML](https://docs.microsoft.com/visualstudio/xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals).  
  
  
Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Pour créer un projet d'application console Visual Basic  
  
1.  Démarrez Visual Studio 2010.  
  
2.  À partir de la **fichier** menu, sélectionnez **New**, puis sélectionnez **projet**. La boîte de dialogue **Nouveau projet** s’affiche. Pour **types de projets**, sélectionnez **autres langages,** , puis sélectionnez **Visual Basic**. Pour **modèles**, sélectionnez Application Console. Puis tapez `XMLLiterals` dans le **nom** champ et un emplacement de projet dans le **emplacement** champ. Cliquez sur **OK**.  
  
     Le nouveau projet est créé. Le projet XMLLiterals contient un fichier source Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Pour ajouter un fichier XSD existant au projet  
  
1.  Ouvrez un nouveau texte de fichiers dans Notepad.Copy le code d’exemple de schéma XML à partir de [schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md) et collez-le dans le fichier.  
  
2.  Enregistrez le fichier à l'emplacement de votre choix avec le nom PurchaseOrderSchema.xsd.  
  
3.  Dans l’Explorateur de solutions, cliquez sur le nom du projet, sélectionnez **ajouter**, puis sélectionnez **un élément existant...** . Le **ajouter un élément existant** boîte de dialogue s’affiche. Accédez au fichier PurchaseOrderSchema.xsd, sélectionnez-le, puis cliquez sur **ajouter**.  
  
     Le projet XMLLiterals contient désormais deux fichiers : Module1.vb et PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Pour ajouter le code Visual Basic avec un littéral XML, selon le fichier XSD inclus dans le projet  
  
1.  Remplacez le code du fichier Module1.vb par le code suivant :  
  
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
  
2.  Avec le bouton droit n’importe quel nœud XML dans un littéral XML ou une importation d’espace de noms XML et sélectionnez **afficher dans l’Explorateur de schémas**.  
  
     L'Explorateur de schémas XML est affiché côte à côte avec un fichier Visual Basic dont le littéral XML est associé au jeu de schémas XML.




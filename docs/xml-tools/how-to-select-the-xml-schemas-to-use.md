---
title: "Comment : sélectionner les schémas XML à utiliser | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 80d0438e7c7dfb7fd346dc5faae6f364279658ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Procédure : sélectionner les schémas XML à utiliser
L'Éditeur XML fournit un cache de schéma dans le répertoire %InstallDir%\Xml\Schemas. Le cache de schéma contient des schémas XML connus utilisés pour IntelliSense et la validation de documents XML.  
  
 Le **schémas** propriété de document est utilisée pour sélectionner un ou plusieurs XML schema definition language (XSD) à utiliser. Elle permet de choisir des schémas dans le cache de schéma ou de spécifier un schéma situé ailleurs dans le cache.  
  
 Les schémas spécifiés sont enregistrés dans le fichier masqué d'options utilisateur de la solution (.suo), avec toutes les autres propriétés de document XML. Vous ne devez donc pas réentrer ces valeurs la prochaine fois que vous ouvrez la solution.  
  
> [!NOTE]
>  L'éditeur peut effectuer la validation à l'aide d'un schéma inline ou d'un schéma dont la référence est fournie par l'attribut `xsd:schemaLocation`. Pour plus d’informations, consultez [Validation de documents XML](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Pour sélectionner un schéma XML dans le cache de schéma  
  
1.  Ouvrez un fichier dans l'éditeur XML.  
  
2.  Dans la fenêtre de propriétés de document, cliquez sur le bouton dans le **schémas** champ.  
  
     Le **schémas XML** boîte de dialogue s’affiche. La boîte de dialogue répertorie tous les schémas portant une extension .xsd dans le cache de schéma (y compris les schémas référencés dans le fichier catalog.xml), et également tout schéma qui se trouve dans la solution actuelle, ouvrir dans Visual Studio, désigné par une `xsd:schemaLocation` d’attribut ou référencés dans le **schémas** propriété.  
  
3.  Sélectionnez les schémas à utiliser pour la validation en effectuant l’une des opérations suivantes :  
  
    -   Sélectionnez un schéma dans le **schémas XML** boîte de dialogue, cliquez sur le **utilisez** colonne, puis sélectionnez **utiliser ce schéma**.  
  
     - ou -  
  
    -   Sélectionnez plusieurs schémas dans le **schémas XML** boîte de dialogue, avec le bouton droit et sélectionnez **utiliser ce schéma**.  
  
4.  Cliquez sur **OK**.  
  
     La liste des schémas sélectionnés est recopiée dans la **schémas** propriété de document.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Pour ajouter un schéma XML au cache de schéma  
  
1.  Dans la fenêtre de propriétés de document, cliquez sur le bouton dans le **schémas** champ.  
  
2.  Cliquez sur **Ajouter**.  
  
     Cette opération ouvre le **ouvrir le schéma XSD** boîte de dialogue.  
  
3.  Recherchez et sélectionnez le ou les schémas à ajouter au cache de schéma.  
  
4.  Cliquez sur **ouvrir**.  
  
     Les schémas sont ajoutés au schéma de mettre en cache et est la **utilisez** colonne a la valeur **utiliser ce schéma**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Pour supprimer un schéma XML du cache de schéma  
  
1.  Dans la fenêtre de propriétés de document, cliquez sur le bouton dans le **schémas** champ.  
  
2.  Sélectionnez le schéma à supprimer, puis cliquez sur **supprimer**.  
  
     Le schéma est supprimé du cache de schéma en mémoire, mais pas du système de fichiers.  
  
    > [!NOTE]
    >  Si vous avez toujours une référence au schéma via un `schemaLocation` un attribut ou une mise en correspondance `targetNamespace` puis **supprimer** ne fonctionnent pas dans cette situation en raison d’une association automatique. Dans ce cas il est recommandé de marquer le schéma en tant que **n’utilisez pas les schémas sélectionnés** dans les **utiliser** colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Cache de schéma](../xml-tools/schema-cache.md)   
 [Boîte de dialogue schémas XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Éditeur XML](../xml-tools/xml-editor.md)
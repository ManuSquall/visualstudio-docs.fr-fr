---
title: "Procédure pas à pas : Utilisation de XSLT Hierarchy | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b0cd7d0567f12a7f1d57bdea765cbf9eb555dd8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Procédure pas à pas : utilisation de XSLT Hierarchy
L’outil XSLT Hierarchy simplifie de nombreuses tâches de développement XML. Une feuille de style XSLT utilise souvent des instructions `includes` et `imports`. La compilation démarre à partir de la feuille de style principale, mais lorsque vous constatez une erreur en compilant une feuille de style XSLT, l'erreur peut provenir d'une autre source que la feuille de style principale. La résolution de l'erreur ou la modification de la feuille de style peut nécessiter l'accès à des feuilles de style incluses ou importées. L'exécution pas à pas de la feuille de style dans le débogueur peut ouvrir des feuilles de style incluses et importées, et vous pouvez ajouter un point d'arrêt à un point dans une ou plusieurs des feuilles de style incluses.  
  
 L'outil XSLT Hierarchy peut aussi s'avérer utile pour placer des points d'arrêt sur les règles de modèle intégrées. Les règles de modèle sont des modèles spéciaux générés pour chaque mode de la feuille de style et appelés par `xsl:apply-templates` lorsqu'aucun autre modèle ne correspond au nœud. Pour implémenter le débogage dans les règles de modèle intégrées, le débogueur XSLT génère le fichier avec les règles dans le dossier temporaire et les compile avec la feuille de style principale. Si vous n'exécutez pas le code pas à pas à partir d'un `xsl:apply-template`, il peut être difficile de trouver les feuilles de style incluses dans la feuille de style principale ou de trouver et ouvrir la feuille de style avec les règles de modèle intégrées.  
  
 L'exemple dans cette rubrique illustre le débogage dans une feuille de style référencée.  
  
### <a name="procedure-title"></a>Intitulé de la procédure  
  
1.  Ouvrez un document XML dans Visual Studio. Cet exemple utilise le document `collection.xml` suivant.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>  
    <COLLECTION>  
      <BOOK>  
        <TITLE>Lover Birds</TITLE>  
        <AUTHOR>Cynthia Randall</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>The Sundered Grail</TITLE>  
        <AUTHOR>Eva Corets</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>Splish Splash</TITLE>  
        <AUTHOR>Paula Thurman</AUTHOR>  
        <PUBLISHER>Scootney</PUBLISHER>  
      </BOOK>  
    </COLLECTION>  
    ```  
  
2.  Ajoutez le `xslincludefile.xsl` suivant :  
  
    ```  
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
          xml:space="preserve">  
  
    <xsl:template match="TITLE">  
       Title - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="AUTHOR">  
       Author - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="PUBLISHER">  
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->  
    </xsl:template>  
  
    </xsl:stylesheet>  
    ```  
  
3.  Ajoutez le fichier `xslinclude.xsl` suivant :  
  
    ```  
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  
      <xsl:output method="xml" omit-xml-declaration="yes"/>  
  
      <xsl:template match="/">  
        <xsl:for-each select="COLLECTION/BOOK">  
          <xsl:apply-templates select="TITLE"/>  
          <xsl:apply-templates select="AUTHOR"/>  
          <xsl:apply-templates select="PUBLISHER"/>  
          <BR/>  
          <!-- add this -->  
        </xsl:for-each>  
      </xsl:template>  
  
      <!-- The following template rule will not be called,  
      because the related template in the including stylesheet  
      is called. If we move this template so that  
      it follows the xsl:include instruction, this one  
      will be called instead.-->  
      <xsl:template match="TITLE">  
        <DIV STYLE="color:blue">  
          Title: <xsl:value-of select="."/>  
        </DIV>  
      </xsl:template>  
  
      <xsl:include href="xslincludefile.xsl" />  
    </xsl:stylesheet>  
    ```  
  
4.  Ajoutez un point d'arrêt à l'instruction : `<xsl:include href="xslincludefile.xsl" />`  
  
5.  Démarrez le débogage.  
  
6.  Lorsque le débogueur s'arrête à l'instruction `<xsl:include href="xslincludefile.xsl" />`, appuyez sur le bouton Pas à pas détaillé. Notez que le débogage peut continuer dans la feuille de style référencée. La hiérarchie est visible et le concepteur affiche le chemin d’accès correct.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Générateur de profils XSLT](../xml-tools/walkthrough-xslt-profiler.md)
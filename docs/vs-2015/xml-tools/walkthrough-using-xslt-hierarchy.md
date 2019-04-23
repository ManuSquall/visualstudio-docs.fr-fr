---
title: 'Procédure pas à pas : À l’aide de XSLT Hierarchy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d662a94a77dff02fd994122e5106f5bff35bac3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669443"
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Procédure pas à pas : À l’aide de XSLT Hierarchy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Procédure pas à pas : Profileur XSLT](../xml-tools/walkthrough-xslt-profiler.md)

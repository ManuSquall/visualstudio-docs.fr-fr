---
title: "Procédure pas à pas : utilisation d'IntelliSense XSLT"
description: Découvrez comment utiliser XSLT IntelliSense pour compléter automatiquement les valeurs de certains attributs en suivant les étapes de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3bb4024c4545dfaae7cdb9faa5d6484a66cd3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875027"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Procédure pas à pas : utilisation d'IntelliSense XSLT

Cette procédure pas à pas montre comment utiliser IntelliSense XSLT pour effectuer la saisie semi-automatique de valeurs de certains attributs.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Pour utiliser IntelliSense dans l'attribut name des éléments xsl:with-param et xsl:call-template

1. Créez un fichier XSLT et copiez le code suivant dans celui-ci :

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2. Insérez votre curseur après `<xsl:template name="msg23" match="msg23">` et appuyez sur **entrée**. Commencez ensuite à taper l'élément `xsl:call-template` suivant :

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     La liste de noms de modèle s'affiche dans l'attribut `name=""` de l'élément `xsl:call-template` à mesure que vous tapez.

3. Insérez votre curseur après `<xsl:call-template name="localized-message">` et appuyez sur **entrée**. Commencez ensuite à taper l'élément `xsl:with-param` suivant :

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     La liste de noms de paramètre s'affiche dans l'attribut `name=""` de l'élément `xsl:with-param`.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Pour utiliser IntelliSense dans l'attribut mode d'un élément xsl:apply-templates

1. Créez un fichier XSLT et copiez le code suivant dans celui-ci :

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Insérez votre curseur après `<xsl:apply-templates select="phone" />` et appuyez sur **entrée**. Commencez ensuite à taper l'élément `xsl: apply-templates` suivant :

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     La liste de modes de modèle s'affiche dans l'attribut `mode=""` de l'élément `xsl:apply-templates`.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Pour utiliser IntelliSense dans les attributs stylesheet-prefix et result-prefix d'un élément xsl:namespace-alias

1. Créez un fichier XSLT et copiez le code suivant dans celui-ci :

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2. Insérez votre curseur après `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` et appuyez sur **entrée**. Commencez ensuite à taper l'élément `xsl:namespace-alias` suivant :

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Notez la façon dont la liste de préfixes est apparue dans les attributs `stylesheet-prefix` et `result-prefix` de l'élément `xsl:namespace-alias`.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités IntelliSense de l’éditeur XML](../xml-tools/xml-editor-intellisense-features.md)

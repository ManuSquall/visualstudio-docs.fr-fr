---
title: 'Didacticiel de l’ancrage-partie 8 : superposition d’images'
description: Comment examiner et gérer des couches d’image dans les images de l’ancrage.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8f669baf6f3275f54c7e4a6ff2b31f9c260b2bb9
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222667"
---
# <a name="image-layering"></a>Superposition d’images

Saviez-vous que vous pouvez voir ce qui compose une image ? À l’aide de la `docker image history` commande, vous pouvez voir la commande qui a été utilisée pour créer chaque couche dans une image.

1. Utilisez la `docker image history` commande pour voir les couches dans l' `getting-started` image que vous avez créée précédemment dans le didacticiel.

    ```bash
    docker image history getting-started
    ```

    Vous devez obtenir une sortie qui ressemble à ceci (les dates/ID peuvent être différents).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Chacune des lignes représente une couche dans l’image. L’affichage affiche la base en bas, avec la couche la plus récente en haut. À l’aide de cela, vous pouvez également voir rapidement la taille de chaque couche, afin de diagnostiquer les images volumineuses.

1. Vous remarquerez que plusieurs lignes sont tronquées. Si vous ajoutez l' `--no-trunc` indicateur, vous obtenez la sortie complète (Oui, vous utilisez un indicateur tronqué pour obtenir une sortie intronquée).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Mise en cache de couche

Maintenant que vous avez vu la couche en action, il existe une leçon importante pour vous aider à réduire les temps de génération de vos images de conteneur.

> Une fois qu’une couche est modifiée, toutes les couches en aval doivent également être recréées

Examinons le fichier dockerfile que vous utilisiez une fois de plus...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

En revenons à la sortie de l’historique de l’image, vous voyez que chaque commande du fichier dockerfile devient une nouvelle couche dans l’image. Vous vous souvenez peut-être que lorsque vous apportez une modification à l’image, les dépendances des fils devaient être réinstallées. Existe-t-il un moyen de résoudre ce problème ? Il n’est pas judicieux d’expédier les mêmes dépendances chaque fois que vous générez des builds, n’est-ce pas ?

Pour résoudre ce problème, vous pouvez restructurer votre fichier dockerfile pour aider à prendre en charge la mise en cache des dépendances. Pour les applications basées sur des nœuds, ces dépendances sont définies dans le `package.json` fichier. Alors, que se passe-t-il si vous avez copié uniquement ce fichier dans un premier temps, si vous installez les dépendances, *puis* que vous copiez dans tout le reste ? Ensuite, vous recréez uniquement les dépendances de fils si une modification a été apportée au `package.json` . Vous êtes logique ?

1. Mettez à jour fichier dockerfile pour copier dans le `package.json` premier, installez les dépendances, puis copiez tout le reste dans.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Générez une nouvelle image à l’aide de `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Une sortie semblable à celle-ci doit s’afficher...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Vous verrez que toutes les couches ont été reconstruites. Tout à fait parfait, puisque vous avez modifié le fichier dockerfile un peu.

1. À présent, apportez une modification au `src/static/index.html` fichier (par exemple, modifiez le pour qu’il indique `<title>` « l’application Isard TODO »).

1. Générez l’image de l’ancrer maintenant à `docker build` nouveau. Cette fois-ci, la sortie doit ressembler à un peu différent.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Tout d’abord, vous remarquerez que la génération a été beaucoup plus rapide ! Vous verrez que les étapes 1-4 ont toutes été `Using cache` . Donc, Hourra ! Vous utilisez le cache de génération. L’envoi et l’extraction de cette image et ses mises à jour seront également beaucoup plus rapides. Hourra!

## <a name="multi-stage-builds"></a>Builds à plusieurs étapes

Bien que nous ne puissions pas vous plonger trop dans ce didacticiel, les builds en plusieurs étapes sont un outil incroyablement puissant pour vous aider à utiliser plusieurs étapes pour créer une image. Il existe plusieurs avantages :

- Séparer les dépendances au moment de la génération des dépendances de Runtime
- Réduire la taille globale de l’image en *n’envoyant que* ce que votre application doit exécuter

### <a name="maventomcat-example"></a>Exemple Maven/Tomcat

Lors de la création d’applications basées sur Java, un JDK est nécessaire pour compiler le code source vers le bytecode Java. Toutefois, ce JDK n’est pas nécessaire en production. En outre, vous pouvez utiliser des outils comme Maven ou Gradle pour aider à générer l’application.
Celles-ci ne sont pas non plus nécessaires dans votre image finale. Aide sur les builds à plusieurs étapes.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Cet exemple utilise une étape (appelée `build` ) pour effectuer la génération Java en cours à l’aide de Maven. La deuxième étape (à partir de `FROM tomcat` ) copie les fichiers de l' `build` étape. L’image finale est uniquement la dernière étape en cours de création (qui peut être remplacée à l’aide de l' `--target` indicateur).

### <a name="react-example"></a>exemple de React

lors de la génération d’applications React, vous avez besoin d’un environnement de nœud pour compiler le code JS (généralement JSX), les feuilles de style SASS, etc. en HTML, JS et CSS statiques. Si vous n’êtes pas en cours de rendu côté serveur, vous n’avez même pas besoin d’un environnement de nœud pour la génération de production. Pourquoi ne pas envoyer les ressources statiques dans un conteneur Nginx statique ?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Ici, vous utilisez une `node:12` image pour effectuer la génération (optimisation de la mise en cache de la couche), puis copiez la sortie dans un conteneur nginx. Cool, n’est-ce pas ?

## <a name="recap"></a>Récapitulatif

En comprenant un peu plus d’informations sur la structure des images, vous pouvez créer des images plus rapidement et envoyer moins de modifications. Les builds à plusieurs étapes permettent également de réduire la taille globale des images et d’augmenter la sécurité finale des conteneurs en séparant les dépendances au moment de la génération des dépendances de Runtime.

## <a name="next-steps"></a>Étapes suivantes

Poursuivez avec le didacticiel.

> [!div class="nextstepaction"]
> [Déploiement dans le Cloud](deploy-to-cloud.md)
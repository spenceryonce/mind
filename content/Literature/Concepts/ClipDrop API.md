curl -X POST https://clipdrop-api.co/portrait-surface-normals/v1 \
     -H 'x-api-key: bbd2f4158b80c68815f102d9a3fb85436196ede4039c0453f0c402b094e56940c86b86cd77df42bbd78bdeba0b7aa04b' \
     -F image_file=@img1.png \
     -o resultnormal.jpg



curl -X POST https://clipdrop-api.co/portrait-depth-estimation/v1 \
-H 'x-api-key: bbd2f4158b80c68815f102d9a3fb85436196ede4039c0453f0c402b094e56940c86b86cd77df42bbd78bdeba0b7aa04b' \
-F image_file=@img1.png \
-o result.jpg

glowing brains floating through a foggy wilderness at night in the rain with snow on the ground and red and blue lights from the christmas tree in the background

curl -X POST https://clipdrop-api.co/super-resolution/v1 \
-H 'x-api-key: bbd2f4158b80c68815f102d9a3fb85436196ede4039c0453f0c402b094e56940c86b86cd77df42bbd78bdeba0b7aa04b' \
-F image_file=@tree.jpg \
-F upscale=2 \
-o treextwo.jpg
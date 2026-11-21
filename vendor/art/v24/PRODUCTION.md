# Anime illustration assets, version 2.3

Created with the built-in image generation tool for this project. Original generated transparent RGBA PNGs were converted to WebP quality 92, method 6, preserving alpha and original 1024×1536 dimensions. The six packaged files total approximately 1.5 MB. No source artwork was sent to an external art service beyond the built-in generation capability.

## Final base prompt template

Use case: stylized-concept. Asset type: single transparent full-body equipped-ready anime RPG character sprite for an offline mobile learning game. Refined anime game illustration, expressive almond eyes, elegant cel shading with rich painted highlights, carefully sculpted fabric folds and hair locks, high production illustration quality, natural six-head human proportions, attractive youthful adult. Front three-quarter very slight turn, face toward viewer, entire head, boots and all limbs clearly visible, centered with comfortable transparent margin. Both arms anatomically connected and bent naturally at elbows, wrists straight. Both empty hands are closed gripping fists, thumbs opposed over curled fingers, seen from front-side so a vertical staff or handle could pass behind fingers at the center of each fist. No open palms or dangling fingers. Put the two fists low near hip height, away from the body silhouette. Do not draw any weapon, staff, wand, hammer, rod, accessory held in hand or energy effect. There must be no object in either fist, just a naturally wrapped gripping pose. Solid crafted clothing and hair, refined contours, anime hero personality, no clay or plastic look. No text, floor, podium, background, labels or shadows outside the character. Truly transparent background. Portrait format.

Character specifications:
- top.webp: Kato, male hardware guardian, tousled chestnut spiky hair, brown eyes, forest green short utility jacket over charcoal tshirt, cargo trousers and brown work boots.
- jungle.webp: Ryn, female Linux infiltrator, black hair tied into a high ponytail, green goggles on forehead, black technical hooded jacket with neon green piping, fitted black cargo pants, black and green boots.
- mid.webp: Elara, female code mage, lavender hair with two braids, purple long tailored open coat with cyan arcane embroidery over teal shirt, dark trousers, purple boots.
- adc.webp: Liam, male network scout, brown hair and yellow cap, amber cropped technical jacket, headphones around neck, charcoal cargo pants, yellow and black boots.
- support.webp: Nala, female support guardian, rose pink braided hair with small white flowers, white and rose armor coat with gold trim, rose skirt firmly attached at waist, white and rose boots.

## Additional Liam rifle-pose edit

Edit only the arm pose of the exact Liam character. Keep his face, yellow cap, hairstyle, headphones, clothes, body proportions, legs, boots, full-body framing and art style unchanged. Keep true transparent background. He is preparing to hold a rifle horizontally across his abdomen. Bend the viewer-left arm into a vertical gripping fist near the abdomen and cross the viewer-right forearm inward into a closed support fist slightly higher. Natural wrists and connected shoulders/elbows. Both fists empty: the game renders the rifle behind the fingers. Do not retain extra arms or hands. Keep the whole character visible.

Observed output fist positions were calibrated individually in anime-illustration.js, rather than assuming the prompt's requested coordinates. The rifle renderer uses an authored metallic vector family so its grip and foregrip fit those positions and never obscure the face. Other weapon families use original packaged art, calibrated pivots and sprite-space silhouette masks. Closed fists are composited last as occlusion masks. Material/gear families are shared; this is not 250 separately painted full characters.

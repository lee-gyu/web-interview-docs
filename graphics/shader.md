# What is Shader?

## GPT 답변

```text
In the context of computer graphics, a shader is a type of program that is used to perform shading - the process of applying light and color to a 3D object.

Shaders play a crucial role in determining the look and feel of objects in 3D graphics, determining things like color, brightness, texture, and special effects. They are primarily used in 3D rendering engines and graphics hardware to provide a high degree of control over the rendering process.

There are several types of shaders, including:

- Vertex Shaders: These are used to manipulate the properties of individual vertices, such as their position, color, or texture coordinates. This happens before the shape is rasterized into pixels.

- Pixel (or Fragment) Shaders: These shaders determine the properties of individual pixels. They take the results from the vertex shader and apply effects like textures, lighting, shadows, and color blending.

- Geometry Shaders: These shaders are used to manipulate entire primitives (such as points, lines, and triangles) and can even create new primitives from existing ones.

- Compute Shaders: These shaders are designed for performing general-purpose computations that don't necessarily need to be tied to vertices or pixels.

Shaders are written in specific shading languages, such as GLSL (OpenGL Shading Language), HLSL (High-Level Shading Language for DirectX), and others. They are usually executed directly on the graphics processing unit (GPU) for efficiency.
```

translated by korean

```text
컴퓨터 그래픽스의 맥락에서 셰이더는 셰이딩(빛과 색을 3D 객체에 적용하는 과정)을 수행하는 프로그램의 한 종류입니다.

셰이더는 3D 그래픽스에서 객체의 외관을 결정하는 데 중요한 역할을 하는데, 색상, 밝기, 텍스처, 특수 효과 등을 결정합니다. 주로 3D 렌더링 엔진과 그래픽스 하드웨어에서 렌더링 과정에 대한 높은 수준의 제어를 제공하기 위해 사용됩니다.

셰이더에는 여러 종류가 있습니다:

버텍스 셰이더: 이들은 개별 버텍스의 속성을 조작하는 데 사용되며, 이는 위치, 색상, 또는 텍스처 좌표와 같은 것들을 포함합니다. 이는 모양이 픽셀로 래스터화되기 전에 발생합니다.

픽셀 (또는 프래그먼트) 셰이더: 이 셰이더는 개별 픽셀의 속성을 결정합니다. 버텍스 셰이더의 결과를 취하고 텍스처, 조명, 그림자, 색상 블렌딩과 같은 효과를 적용합니다.

지오메트리 셰이더: 이 셰이더는 전체 기본 요소(점, 선, 삼각형 등)를 조작하는 데 사용되며, 기존의 것에서 새로운 기본 요소를 생성할 수도 있습니다.

컴퓨트 셰이더: 이 셰이더는 버텍스나 픽셀에 반드시 연결될 필요가 없는 일반적인 계산을 수행하도록 설계되었습니다.

셰이더는 GLSL (OpenGL 셰이딩 언어), HLSL (DirectX를 위한 고수준 셰이딩 언어) 등의 특정 셰이딩 언어에서 작성되며, 효율성을 위해 일반적으로 그래픽스 처리 유닛 (GPU)에서 직접 실행됩니다.
```

## links

- <https://en.wikipedia.org/wiki/Shader>

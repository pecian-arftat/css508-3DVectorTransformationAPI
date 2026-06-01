
<h1> <b>COMMON ISSUES</b> </h1>

<h2 id="About"> About </h2>
<p>
The purpose of this document is to list and explain possible common issues that may arise when turning my mock project into production. 
</p>

<h2> <b>Table of Contents</b> </h2>
<ul>
    <!-- Need to remove anchor or further test to check if it works on GitHub. -->
    <li><a href="FloatingPoint">Floating-Point Precision Errors</a></li>
    <li><a href="GimbalLock">Gimbal Lock</a></li>
    <li><a href="PerformanceBottlenecks">Performance Bottlenecks</a></li>
    <li><a href="SIMD">SIMD / Hardware Compatibility Issues</a></li>
    <li><a href="CoordinateSystem">Coordinate System Mismatches</a></li>
    <li><a href="Interoperability">Interoperability Problems</a></li>
    <li><a href="ThreadSafety">Thead Safety Problems</a></li>
    <li><a href="MemoryManagement">Memory Management Issues</a></li>
    <li><a href="NumericalStability">Numerical Instability at Large Coordinates</a></li>
    <li><a href="InvalidUserInput">Invalid User Inputs</a></li>
    <li><a href="Misunderstanding">API Misunderstanding</a></li>
    <li><a href="Dependency">Dependency / Compiler Issues</a></li>
    <li><a href="Ranking">Ranking Most Common Issues</a></li>
</ul>

<h2 id="FloatingPoint"> Floating-Point Precision Errors</h2>
<p>
This issue will be the most common issue. It will have the following symptoms. 
    <ul>
        <li>Objects slowly drift over time</li>
        <li>Rotations become unstable</li>
        <li>Tiny gaps between geometry</li>
        <li>Animation jitter</li>
        <li>Physics instability</li>
    </ul>
</p>

<h2 id="GimbalLock">Gimbal Lock</h2>
<p>
Gimbal locking is a phenomenon where a 90-degree rotation of an axis around the x, y, or z axis causes the other two axes to align and become unusable. For example, if an object is rotated 90 degrees around the x-axis, the y- and z-axes will align. Then, rotating the object around the y or z axis (for instance, around the y axis) will cause the other axes to rotate together in the same direction (the z axis will also rotate along with the y axis).

The following will be some symptoms of gimbal lock:
    <ul>
        <li>Sudden axis locking</li>
        <li>Unexpected rotation behavior</li>
        <li>Animation glitches</li>
    </ul>
</p>

<h2 id="PerformanceBottlenecks">Performance Bottlenecks</h2>
<p>
Math APIs are called millions of times per frame in production. Potential problems, such as excessive memory allocation and slow quaternion normalization, may lead to the following symptoms: 
    <ul>
        <li>FPS drops</li>
        <li>Input lag</li>
        <li>Simulation slowdown</li>
    </ul>
</p>

<h2 id="SIMD">SIMD / Hardware Compatibility Issues</h2>
<p>
Production engines often optimize using SSE (Streaming SIMD Extensions), AVX (Advanced Vector Extensions), and NEON. If not optimized using the extensions, following issues will occur: 
    <ul>
        <li>Different floating-point results across CPUs</li>
        <li>Alignment crashes</li>
        <li>Platform-specific bugs</li>
    </ul>
</p>

<h2 id="CoordinateSystem">Coordinate System Mismatches</h2>
<p>
Graphic engines often have a different coordinate system for performance or to keep high maintainability. If there is a coordinate system mismatch, there will be the following issues: 
    <ul>
        <li>Inverted models</li>
        <li>Mirrored rotations</li>
        <li>Backward movements</li>
    </ul>
</p>

<h2 id="Interoperability">Interoperability Problems</h2>
<p>
Many graphics developers use different APIs. If proper integration methods are not established, there will be the following issues: 
    <ul>
        <li>Matrix convention mismatches</li>
        <li>Row-major vs column-major confusion</li>
        <li>Degree/radian inconsistencies</li>
    </ul>
</p>

<h2 id="ThreadSafety">Thread Safety Problems</h2>
<p>
Many rendering engines are highly parallel. If the API does not have a proper implementation for parallelism, there will be the following issues: 
    <ul>
        <li>Race conditions</li>
        <li>Shared transformation corruption</li>
        <li>Nondeterministic behavior</li>
    </ul>
</p>

<h2 id="MemoryManagement">Memory Management Issues</h2>
<p>
In production, there will be millions of API calls. If memory management is poor, there will be the following issues: 
    <ul>
        <li>Frame stuttering</li>
        <li>High RAM usage</li>
        <li>Poor Scalability</li>
    </ul>
</p>

<h2 id="NumericalStability">Numerical Instability at Large Coordinates</h2>
<p>
If instability is found at large coordinates, it will be a huge issue for developers of open-world games, GIS systems, CAD software, and simulations. 

Below are some symptoms that developers might encounter: 
    <ul>
        <li>Geometry shaking</li>
        <li>Camera jitter</li>
        <li>Broken collision detection</li>
    </ul>
</p>

<h2 id="InvalidUserInput">Invalid User Input</h2>
<p>
Production users might misuse the API. The risk here is silent corruption—using the API incorrectly without causing an immediate crash. The program continues to run, spreading the wrong output.  
</p>

<h2 id="Misunderstanding">API Misunderstanding</h2>
<p>
Simple yet often issue. They are: 
    <ul>
        <li>Degrees vs Radians</li>
        <li>Rotation order</li>
        <li>Quaternion multiplication order</li>
    </ul>
</p>

<h2 id="Dependency"> Dependency / Compiler Issues</h2>
<p>
Production builds often differ from development. 

Issues: 
    <ul>
        <li>Compiler optimization differences</li>
        <li>Undefined behavior exposed</li>
        <li>Library conflicts</li>
    </ul>
</p>

<h2 id="Ranking"> Most Common Issue Ranking</h2>
<p>
<table>
  <thead>
    <tr>
      <th>Rank</th>
      <th>Issue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Floating-point precision drift</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Rotation convention confusion</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Performance bottlenecks</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Gimbal lock</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Cross-platform inconsistencies</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Invalid input handling</td>
    </tr>
    <tr>
      <td>7</td>
      <td>Coordinate system mismatches</td>
    </tr>
    <tr>
      <td>8</td>
      <td>Documentation misunderstandings</td>
    </tr>
  </tbody>
</table>

</p>
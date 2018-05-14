# Reverberation_Eric-A.-Lehmann
Reverberation coding in Matlab referring to work of Eric A. Lehmann

## old

#### MakeIMResp.m 


 * 函数功能<br>  
    计算对应房间参数的冲击响应及其频域形式<br>
 * 核心公式<br>  
     <img src="https://latex.codecogs.com/gif.latex?h(t)&space;=&space;\sum_{u=0}^{1}\sum_{l=-\infty}^{\infty}A(u,l)\delta&space;(t&space;-&space;\tau(u,l)))"> <br>
     <br>
     &nbsp; <img src="https://latex.codecogs.com/gif.latex?A(u,l)&space;=&space;\frac{\beta_{x,1}^{\left&space;|&space;l-u&space;\right&space;|}&space;\beta_{x,2}^{\left&space;|&space;l&space;\right&space;|}&space;\beta_{y,1}^{\left&space;|&space;m-v&space;\right&space;|}&space;\beta_{y,2}^{\left&space;|&space;m&space;\right&space;|}&space;\beta_{z,1}^{\left&space;|&space;n-w&space;\right&space;|}&space;\beta_{z,2}^{\left&space;|&space;n&space;\right&space;|}}{4\pi&space;d(u,l))}"><br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?\tau&space;(u,l)&space;=&space;d(u,l)/c" /><br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?d(u,l)&space;=&space;\left&space;\|&space;diag(2u-1,2v-1,2w-1)\cdot&space;P_{s}&space;&plus;&space;P_{r}-&space;diag(2l,2m,2n)&space;\right&space;\|" /><br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?P_{s}&space;=&space;\left&space;[&space;x_{s},y_{s},z_{s}\right&space;]&space;^{T}" />  : 声源位置<br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?P_{r}&space;=&space;\left&space;[&space;x_{r},y_{r},z_{r}\right&space;]&space;^{T}" />  : 接收器位置<br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?r&space;=&space;\left&space;[&space;L_{x},L_{y},L_{z}\right&space;]&space;^{T}"  />  : 房间尺寸<br>
     <br>
     &nbsp;<img src="https://latex.codecogs.com/gif.latex?\beta" /> : 房间墙壁反射系数<br>
     

 * 思路总结<br> 
    * 根据Sabine公式估算混响时间；<br>
    * for a=0:1<br>
       &nbsp;&nbsp;for b=0:1<br>
        &nbsp;&nbsp;&nbsp;&nbsp;for c = 0:1<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;改变l,调用Check_lDim(...)<br>
        &nbsp;&nbsp; &nbsp;&nbsp;end<br>
       &nbsp;&nbsp;end<br>
      end<br>
    * Check_lDim(...)改变m,调用Check_nDim(...)<br>
     * Check_nDim(...)改变n,计算h；并验证是否大于预设的停止计算时间（与混响时间成比例关系）<br>
    
    
    

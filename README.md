# NOTE
### gemm-multi-stage_e4m3_v2.cu is my modified code for support FP8. The step to reproduction
```bash
1. git clone git@github.com:Godlovecui/cute-gemm.git
2. make -j
```
## It will raise below errors in make phase
`
3rd/cutlass/include/cute/atom/copy_traits_sm80.hpp(160): error: static assertion failed with "In CopyAtom, dst layout doesn't vectorize into registers. This dst layout is incompatible with this tiled copy."
      static_assert(decltype(size(rD) == Int<1>{})::value, "In CopyAtom, dst layout doesn't vectorize into registers. This dst layout is incompatible with this tiled copy.")
      ^
          detected during:                                                                                                                                          instantiation of "void cute::copy_unpack(const cute::Copy_Traits<cute::SM80_CP_ASYNC_CACHEGLOBAL_ZFILL<cutlass::uint128_t, cutlass::uint128_
t>> &, const cute::Tensor<TS, SLayout> &, cute::Tensor<TD, DLayout> &) [with TS=cute::ViewEngine<cute::gmem_ptr<cutlass::float_e4m3_t *>>, SLayout=cute::Layout<cute::tuple<cute::tuple<cute::_16, cute::_1>>, cute::tuple<cute::tuple<cute::_1, cute::C<0>>>>, TD=cute::ViewEngine<cute::smem_ptr<cutlass::floa
t_e4m3_t *>>, DLayout=cute::Layout<cute::tuple<cute::tuple<cute::tuple<cute::_8, cute::_2>, cute::C<1>>>, cute::tuple<cute::tuple<cute::tuple<cute::_1,
int>, cute::_0>>>]" at line 106 of 3rd/cutlass/include/cute/atom/copy_atom.hpp
            instantiation of "void cute::Copy_Atom<cute::Copy_Traits<Args...>, CopyInternalType>::call(const cute::Tensor<SEngine, SLayout> &, cute::Tensor<DEngine, DLayout> &) const [with Args=<cute::SM80_CP_ASYNC_CACHEGLOBAL_ZFILL<cutlass::uint128_t, cutlass::uint128_t>>, CopyInternalType=cutlass::float_e4m3_t, SEngine=cute::ViewEngine<cute::gmem_ptr<cutlass::float_e4m3_t *>>, SLayout=cute::Layout<cute::tuple<cute::tuple<cute::_16, cute::_1>>, cute::tuple<cute::tuple<cute::_1, cute::C<0>>>>, DEngine=cute::ViewEngine<cute::smem_ptr<cutlass::float_e4m3_t *>>, DLayout=cute::Layout<cute::tuple<cute::tuple<cute::tuple<cute::_8, cute::_2>, cute::C<1>>>, cute::tuple<cute::tuple<cute::tuple<cute::_1, int>, cute::_0>>>]" at line 127 of 3rd/cutlass/include/c
ute/atom/copy_atom.hpp 
`

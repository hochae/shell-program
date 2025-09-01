```vim

" 기본 설정
set nocompatible
set encoding=utf-8
set fileencoding=utf-8

" 화면 표시 설정
set t_u7=
set number              " 줄 번호 표시
set cursorline          " 현재 줄 하이라이트
set showmatch           " 괄호 매칭 표시
set ruler               " 커서 위치 표시
set laststatus=2        " 상태바 항상 표시
set showcmd             " 명령어 표시
set wildmenu            " 명령행 자동완성
set scrolloff=3         " 스크롤 여백

" 들여쓰기 및 탭 설정
set autoindent          " 자동 들여쓰기
set smartindent         " 스마트 들여쓰기
set cindent             " C언어 스타일 들여쓰기
set tabstop=4           " 탭 크기
set shiftwidth=4        " 자동 들여쓰기 크기
set expandtab           " 탭을 스페이스로 변환
set smarttab            " 스마트 탭

" 검색 설정
set hlsearch            " 검색 결과 하이라이트
set incsearch           " 점진적 검색
set ignorecase          " 대소문자 구분 안함
set smartcase           " 대문자 포함시 대소문자 구분

" 편집 설정
set backspace=2         " 백스페이스 설정
set autoread            " 파일 변경시 자동 읽기
" set clipboard=unnamed   " 시스템 클립보드 사용 (macOS)
set clipboard=unnamedplus  " 시스템 클립보드 사용 (Linux)

" 백업 및 스왑파일 설정
set nobackup
set noswapfile
set nowritebackup

" 안개낀 Dark Theme 색상 설정
set background=dark
syntax enable

" 커스텀 색상 테마 (안개낀 어두운 느낌)
highlight Normal          ctermfg=252 ctermbg=235 guifg=#d0d0d0 guibg=#262626
highlight LineNr          ctermfg=240 ctermbg=235 guifg=#585858 guibg=#262626
highlight CursorLine      cterm=NONE ctermbg=236 guibg=#303030
highlight CursorLineNr    ctermfg=250 ctermbg=236 guifg=#bcbcbc guibg=#303030
highlight Visual          ctermbg=238 guibg=#444444
highlight Comment         ctermfg=244 guifg=#808080 gui=italic
highlight String          ctermfg=150 guifg=#afd787
highlight Number          ctermfg=180 guifg=#d7af87
highlight Keyword         ctermfg=110 guifg=#87afd7 gui=bold
highlight Function        ctermfg=222 guifg=#ffd787
highlight Type            ctermfg=179 guifg=#d7af5f gui=bold
highlight PreProc         ctermfg=176 guifg=#d787d7
highlight Special         ctermfg=174 guifg=#d78787
highlight Error           ctermfg=196 ctermbg=235 guifg=#ff0000 guibg=#262626
highlight Search          ctermfg=0 ctermbg=11 guifg=#000000 guibg=#ffff00
highlight MatchParen      ctermfg=15 ctermbg=8 guifg=#ffffff guibg=#808080

" 상태바 색상
highlight StatusLine      ctermfg=15 ctermbg=240 guifg=#ffffff guibg=#585858
highlight StatusLineNC    ctermfg=7 ctermbg=8 guifg=#c0c0c0 guibg=#808080

" C언어 특화 설정
augroup c_programming
    autocmd!
    autocmd FileType c,cpp setlocal cindent
    autocmd FileType c,cpp setlocal cinoptions=:0,l1,g0,t0,(0,W4
    autocmd FileType c,cpp setlocal textwidth=80
    autocmd FileType c,cpp setlocal colorcolumn=80
augroup END

" 컴파일 및 실행 단축키
autocmd FileType c map <F9> :w<CR>:!gcc -o %< % && ./%<<CR>
autocmd FileType cpp map <F9> :w<CR>:!g++ -o %< % && ./%<<CR>

" 유용한 키 매핑
" ESC로 검색 하이라이트 제거


" 창 이동 단축키
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

" 괄호 자동완성
inoremap ( ()<left>
inoremap [ []<left>
inoremap { {}<left>
inoremap " ""<left>




" C언어 코드 템플릿
nnoremap <leader>c :-1read $HOME/.vim/templates/template.c<CR>

" 주석 토글 (Ctrl+/)
noremap <C-_> :call ToggleComment()<CR>
function! ToggleComment()
    if getline('.') =~ '^\s*//'
        s/^\(\s*\)\/\//\1/
    else
        s/^\(\s*\)/\1\/\//
    endif
endfunction

" 자동완성 설정
set complete+=k         " 사전 파일에서 완성
set completeopt=menuone,longest,preview

" 파일 형식별 들여쓰기
filetype plugin indent on

" C언어 문법 확장
let c_comment_strings=1
let c_gnu=1
let c_space_errors=1

" 80열 표시
" set colorcolumn=80
highlight ColorColumn ctermbg=237 guibg=#3a3a3a

" 공백 문자 표시 (선택사항)
" set list
" B
" set listchars=tab:▸\ ,eol:¬,trail:⋅

" 상태바 정보 표시
set statusline=%f\ %m%r%h%w\ [%{&ff}]\ [%Y]\ [%04l,%04v]\ [%p%%]\ [%L\ lines]

" 폴딩 설정
set foldmethod=syntax
set foldlevelstart=99

" 마우스 지원 (터미널에서 사용시)
if has('mouse')
    set mouse=a
endif

```